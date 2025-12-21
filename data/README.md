# Dados do Projeto

Este projeto utiliza dados intraday do contrato futuro de índice (WINFUT),
processados em ambiente Databricks.

## Observação Importante

Os dados brutos e intermediários **não estão versionados neste repositório**,
pois são armazenados e processados diretamente no ambiente de dados em nuvem
(Databricks / DBFS), seguindo boas práticas de engenharia de dados.

## Origem dos Dados

- Fonte: Arquivos CSV históricos do WINFUT
- Frequência: Timeframes intraday (5m, 15m, 60m)
- Ambiente de armazenamento: Databricks Volumes (DBFS)

## Reprodutibilidade

Toda a lógica de ingestão, transformação e modelagem pode ser reproduzida
a partir do notebook disponível em:

[ -src/notebooks/mvp-winfut-databricks-pipeline.ipynb](https://github.com/cpjost/MVP-PUC-RIO-1/blob/main/src/notebooksmvp-winfut-databricks-pipeline.ipynb)

