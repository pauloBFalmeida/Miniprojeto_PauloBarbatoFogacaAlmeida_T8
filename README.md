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

## Como executar
1. Abra `Miniprojeto_PauloBarbatoFogaçadeAlmeida_T8.ipynb` no Google Colab ou Jupyter.
2. Execute todas as células (Ambiente de execução → Executar tudo). O CSV é baixado automaticamente com `kagglehub`.
3. Se o download falhar, baixe o CSV no Kaggle e coloque-o na mesma pasta do notebook com o nome `varejo.csv`.
4. O arquivo `varejo_limpo.csv` é gerado na mesma pasta, sem coluna de índice.

## Arquivos
- `Miniprojeto_PauloBarbatoFogaçadeAlmeida_T8.ipynb`: código comentado
- `varejo_limpo.csv`: base tratada
- `README.md`: este documento
