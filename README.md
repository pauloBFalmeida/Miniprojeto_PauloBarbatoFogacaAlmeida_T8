# Mini Projeto - Paulo Barbato Fogaça Almeida - T8

**Aluno(a):** Paulo Barbato Fogaça de Almeida  
**Turma:** T8  
**Curso:** Análise de Dados com Python – Módulo 1, Semana 07

## Objetivo
Realizar uma Análise Exploratória de Dados (AED) da base Varejo: diagnosticar a qualidade, limpar e padronizar os dados,
calcular estatísticas e agrupamentos e exportar uma base tratada (`varejo_limpo.csv`).

## Origem da base
- Kaggle: https://www.kaggle.com/datasets/namespaiva/base-varejo
- Versão utilizada: Vesão 1.0
- Arquivo de entrada: `varejo.csv` (separador `;`). Cada linha representa um **item de compra**.

## Significado das colunas utilizadas
A base não tem dicionário de dados; os significados abaixo foram **inferidos** dos nomes e dos valores.

| Coluna | Significado (inferido) |
|---|---|
| `DATA` | data do registro (mantida como texto) |
| `CO_ID` | identificador da compra |
| `CL_ID` | identificador do cliente |
| `CL_GENERO` | gênero do cliente |
| `CL_EC` | código de estado civil do cliente |
| `CL_FHL` | número de filhos do cliente |
| `CL_SEG` | segmento do cliente |
| `PR_ID` | identificador do produto |
| `PR_CAT` | categoria do produto |
| `PR_NOME` | nome do produto |

## Decisões de limpeza
|Problema|Quantidade|Decisão|Justificativa|
|---|---|---|---|
|Colunas 100% vazias|4|Removidas|Não contêm nenhuma informação|
|Valores ausentes nas colunas com dados|0|Nada a tratar|Nenhum valor ausente encontrado|
|Linhas duplicadas completas|96553|Removidas|Idênticas em todas as colunas \(inclui ids e data\); compras distintas do mesmo cliente foram preservadas|
|Textos vazios ou só com espaços|0|Nada a tratar|Nenhum encontrado|
|Variações de caixa/espaços|0|Padronização aplicada|Evita contar a mesma categoria como valores diferentes|
|CL\_FHL diferente para o mesmo cliente|0|Nada a tratar|Valor consistente por cliente|

Registros antes: 830.000 | depois: 733.447 | colunas antes: 14 | depois: 10.

## Explicação do processo
A **leitura** ocorre na seção 1 do notebook (`pd.read_csv` com `sep=";"`).

A **transformação** ocorre na seção 2, pela função
`tratar_dados` (remoção de colunas vazias, padronização de texto e remoção de duplicatas completas); a análise usa as funções
`resumir` e `diagnostico`. 

A **gravação** ocorre na seção 5 Exportação (`to_csv(index=False)`). 

A padronização do texto e a remoção das
colunas vazias deixaram a base sem colunas inúteis e com categorias escritas de forma única, o que evita contar a mesma
categoria como grupos diferentes nos agrupamentos. Como cada cliente aparece em várias linhas, a estatística de CL_FHL
foi calculada com uma linha por cliente, para que quem compra mais itens não pese mais na média.

## Conclusões
1. A limpeza removeu 4 colunas sem nenhuma informação e 96.553 linhas repetidas em todas as colunas (11,6% dos registros). A base passou de 830.000 registros e 14 colunas para 733.447 registros e 10 colunas.

2. Cada linha é um item de uma compra. São 733.447 linhas, 18.471 compras e 1.000 clientes distintos (média de 39,71 itens por compra). Por isso, contar linhas não é o mesmo que contar compras ou clientes.

3. Por gênero, o número de clientes distintos é: 'f': 519 (51,9%), 'm': 481 (48,1%). O maior grupo é 'f'.

4. CL_FHL é uma característica do cliente, então a análise usa cada cliente uma única vez (1.000 clientes). A média é 1,14, variando de 0 a 4, e 47,3% dos clientes têm CL_FHL maior ou igual a 1.

### Recomendação

Concentrar o planejamento de estoque e as campanhas na categoria que mais vende e corrigir na origem os registros sem categoria definida.

### Limitações

A base não tem valor em R$ nem quantidade, então não é possível medir faturamento. 

Cada linha é um item, e não um cliente. 

Os significados de CL_FHL, CL_EC e CL_SEG foram inferidos pelos nomes das colunas, e a DATA não foi convertida.


## Como executar
1. Abra `Miniprojeto_PauloBarbatoFogaçadeAlmeida_T8.ipynb` no Google Colab ou Jupyter.
2. Execute todas as células (Ambiente de execução → Executar tudo). O CSV é baixado automaticamente com `kagglehub`.
3. Se o download falhar, baixe o CSV no Kaggle e coloque-o na mesma pasta do notebook com o nome `varejo.csv`.
4. O arquivo `varejo_limpo.csv` é gerado na mesma pasta, sem coluna de índice.

## Arquivos
- `Miniprojeto_PauloBarbatoFogaçadeAlmeida_T8.ipynb`: código comentado
- `varejo_limpo.csv`: base tratada
- `README.md`: este documento
