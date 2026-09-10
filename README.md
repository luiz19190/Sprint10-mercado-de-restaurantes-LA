# Sprint 10 — Mercado de Restaurantes em Los Angeles

Projeto do curso de Data Analytics da [TripleTen](https://tripleten.com/), por **Luiz Trajano**.

Pesquisa de mercado sobre os restaurantes de Los Angeles, feita para apoiar uma decisão de
investimento: a abertura de uma pequena cafeteria com garçons robôs. Os investidores querem saber
se o negócio se sustenta depois que o efeito novidade passar — ou seja, se **tipo de
estabelecimento** e **número de assentos** escolhidos batem com o que o mercado de LA mostra, e se
o modelo tem espaço para virar rede.

> ✅ **Status:** projeto concluído. Passos 1 e 2 escritos com conclusão em cada etapa, seção 3 com
> as recomendações finais e seção 4 com o deck de 8 slides para investidores, em PDF.

## Estrutura do projeto

```
├── Sprint 10 - Mercado de Restaurantes LA.ipynb   # notebook principal
├── Data/
│   └── rest_data_us_upd.csv    # estabelecimentos de LA (nome, tipo, rede, endereço, assentos)
├── images/                     # gráficos exportados, usados na apresentação
├── presentation/
│   └── Sprint10-apresentacao-mercado-restaurantes-LA.pdf   # deck de 8 slides para investidores
├── .gitignore
├── LICENSE                     # MIT
└── README.md
```

## Os dados

`rest_data_us_upd.csv` — 9.651 registros de estabelecimentos de Los Angeles; 9.592 depois de remover
3 registros sem `chain` e 56 duplicados.

| coluna | descrição |
|---|---|
| `id` | identificador do registro (não consta do dicionário oficial do projeto) |
| `object_name` | nome do estabelecimento |
| `address` | endereço |
| `chain` | pertence a uma rede (TRUE/FALSE) |
| `object_type` | tipo de estabelecimento |
| `number` | número de assentos |

## Roteiro da análise

**Passo 1 — Preparação.** Grão dos dados, valores ausentes, duplicados explícitos e implícitos,
tipos e plausibilidade dos valores.

**Passo 2 — Análise.** Nove perguntas, cada uma com conclusão própria:

| # | Pergunta |
|---|---|
| 2.1 | Proporção dos tipos de estabelecimento |
| 2.2 | Proporção de rede vs. não-rede |
| 2.3 | Que tipo de estabelecimento é típico para redes |
| 2.4 | O que caracteriza uma rede: muitas unidades pequenas ou poucas grandes |
| 2.5 | Número médio de assentos por tipo |
| 2.6 | Extração do nome da rua a partir do endereço |
| 2.7 | As dez ruas com mais restaurantes |
| 2.8 | Ruas com um único restaurante |
| 2.9 | Distribuição de assentos nas ruas movimentadas |

**Passo 3 — Apresentação.** Deck de 8 slides para investidores em PDF:
[`presentation/Sprint10-apresentacao-mercado-restaurantes-LA.pdf`](presentation/Sprint10-apresentacao-mercado-restaurantes-LA.pdf).

## Principais achados

- **LA é uma cidade de restaurantes.** `Restaurant` é 75,2% dos 9.592 estabelecimentos.
  `Cafe` são 426, 4,4% do mercado, terceiro entre seis tipos e o maior da cauda.
- **Café é o formato que mais vira rede.** 60,6% dos cafés pertencem a alguma rede, contra 37,9% da
  cidade, e a marca de café tem 4,53 unidades em média, a maior replicação de todos os tipos.
- **Mas, acima de 9 lojas, só existem as duas gigantes.** Das 57 marcas, Starbucks (119 unidades) e
  Coffee Bean (55) concentram 67,4% de tudo, 15 têm de 2 a 9 lojas e 40 têm uma loja só. Entre 10 e
  54 unidades não há nenhuma marca.
- **Tamanho de rede e tamanho de loja são independentes.** Pearson -0,001, Spearman 0,019. Crescer
  em unidades não exige loja maior.
- **O mercado é concentrado.** 46,2% das ruas têm um único estabelecimento e somam 3,9% da oferta;
  na outra ponta, 5,6% das ruas concentram 59,5%.
- **A rua não define o tamanho da loja, o tipo define.** Entre tipos a mediana vai de 18 a 29
  assentos; entre rua movimentada e o resto da cidade, de 26 para 28.
- **A coluna de assentos é sintética.** Não há nenhum registro entre 50 e 60 assentos, confirmado no
  arquivo original, então toda a análise usa mediana e não média.

## Recomendação

**Tipo:** café. É o formato com maior taxa de rede (60,6%) e maior replicação por marca (4,53
unidades), e o mais homogêneo dos seis, único com dispersão menor que a própria média (0,86).

**Assentos: de 20 a 25.** Três medidas convergem: a mediana dos cafés de LA é 20, a dos cafés em rua
movimentada é 22,5, e as duas redes que escalaram operam com 25 (Starbucks) e 22 (Coffee Bean).

**Rede: recomendo, com condição.** O mercado comporta e o formato escala, mas entre 10 e 54
unidades não há nenhuma rede de café. A decisão exige um gatilho definido desde o início, quantas unidades em quanto
tempo, com o capital reservado antes da primeira.

O raciocínio completo, com as evidências apontando para cada passo numerado, está na seção 3 do
notebook.

## Histórico de correções

- **2026-09-10.** Conferência do projeto contra os dados recalculados do CSV. O slide 4 do deck, este
  README e o notebook (2.1, 2.3, 3.4 e 4) diziam que não existe rede de café média, "ou 1 loja, ou
  119". Isso não se sustenta: a Coffee Bean tem 55 lojas e 15 marcas têm de 2 a 9. O vazio real é
  de 10 a 54 unidades. Também corrigidos Fast Food (11,1%, não 11,0%), Bakery (3,0%, não 2,9%) e o
  roteiro `outline.md`, que era citado aqui mas não existe no repositório.

## Tecnologias utilizadas

- Python (pandas, numpy)
- **seaborn** — biblioteca principal de visualização deste projeto
- matplotlib — base e ajustes finos
- plotly — gráficos interativos onde a interatividade agrega
- kaleido — exporta os gráficos plotly como PNG para a apresentação
- Jupyter Notebook

## Como executar

1. Clone o repositório.
2. Instale as dependências: `pip install pandas numpy matplotlib seaborn plotly kaleido`
   O `kaleido` só é necessário para exportar os gráficos plotly como PNG. Sem ele o
   notebook roda normalmente e os gráficos aparecem, mas a célula que salva o PNG falha.
3. Abra `Sprint 10 - Mercado de Restaurantes LA.ipynb` e execute as células em ordem.

O caminho do arquivo é controlado pela variável `path` na célula de setup — basta trocar essa linha
para rodar na sua plataforma.
