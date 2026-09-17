# Análise de Preços de Materiais de Construção — Economiza Alagoas

Projeto de análise exploratória de dados utilizando informações reais
obtidas por meio da API pública do Economiza Alagoas.

O objetivo é analisar preços de materiais de construção comercializados
em Maceió, realizando desde a coleta dos dados até etapas de limpeza,
padronização, análise estatística e identificação de possíveis outliers.

## Objetivo

Explorar a variação de preços de materiais de construção e identificar
problemas de qualidade e inconsistências presentes nos dados retornados
pela API.

Os materiais analisados foram:

- Cimento
- Areia
- Brita
- Tijolo
- Tinta

## Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Requests
- Matplotlib
- Seaborn
- Jupyter Notebook
- Visual Studio Code

## Fonte dos dados

Os dados foram obtidos através da API pública do Economiza Alagoas,
disponibilizada pela Secretaria da Fazenda do Estado de Alagoas.

As consultas foram realizadas considerando estabelecimentos localizados
no município de Maceió.

## Etapas do projeto

O projeto foi desenvolvido nas seguintes etapas:

1. Consumo da API do Economiza Alagoas
2. Coleta dos registros
3. Transformação das respostas JSON em DataFrame
4. Análise da qualidade dos dados
5. Tratamento de valores ausentes
6. Conversão de tipos de dados
7. Análise de descrições, unidades e NCMs
8. Padronização dos produtos
9. Estatísticas descritivas
10. Identificação de possíveis outliers pelo método IQR
11. Visualização dos dados
12. Interpretação dos resultados

## Qualidade e padronização dos dados

Durante a análise foi identificado que uma busca textual simples nem
sempre retorna produtos diretamente comparáveis.

Por exemplo, a pesquisa por "CIMENTO" também retornava produtos como
revestimentos de cimento queimado, diferentes tamanhos de embalagem e
outros itens contendo a palavra cimento em sua descrição.

Situações semelhantes foram encontradas nos demais materiais.

Por esse motivo, foram utilizadas informações como:

- NCM
- descrição do produto
- unidade de medida
- volume ou peso da apresentação

para construir grupos de produtos mais comparáveis.

Exemplos de padronização:

- Cimento: apresentação de 50 kg
- Areia: comercialização por volume
- Brita: comercialização por volume
- Tijolo: tijolo cerâmico de 8 furos
- Tinta: embalagem de 18 litros

Após o processo de padronização, a base utilizada na análise exploratória
ficou com 350 registros.

## Análise exploratória

Foram utilizadas medidas como:

- média
- mediana
- mínimo
- máximo
- desvio-padrão
- amplitude
- coeficiente de variação

Também foram construídas visualizações como:

- boxplot
- histograma
- KDE
- distribuições individuais por material

## Outliers

Os possíveis valores atípicos foram identificados utilizando o método
do intervalo interquartil (IQR).

Foram encontrados 28 possíveis outliers:

- Tinta: 20
- Cimento: 7
- Tijolo: 1
- Areia: 0
- Brita: 0

Os registros não foram removidos automaticamente. Eles foram mantidos
para análise, pois valores extremos podem representar diferenças reais
entre marcas, estabelecimentos ou condições de comercialização.

## Principais resultados

A Tinta apresentou a maior dispersão absoluta dos preços, com
desvio-padrão de aproximadamente R$ 155,98.

O Cimento apresentou a menor variabilidade relativa entre os produtos
analisados.

O Tijolo apresentou um valor bastante superior aos demais registros da
categoria, sendo identificado como possível outlier.

A média geral dos preços analisados foi de aproximadamente R$ 275,17,
enquanto a mediana foi de R$ 270,92.

## Estrutura do projeto

```text
economiza-alagoas-data-analysis/
│
├── README.md
├── analise_economiza_alagoas.ipynb
├── dados_economiza_alagoas_brutos.csv
├── requirements.txt
└── .gitignore
