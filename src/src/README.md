# Código-Fonte do MVP

Esta pasta contém os códigos utilizados para construção do pipeline analítico,
processamento dos dados intraday do WINFUT e geração dos resultados apresentados
no MVP.

## Notebook Principal

### `mvp-winfut-databricks-pipeline.ipynb`

Notebook desenvolvido no ambiente Databricks contendo todas as etapas do projeto:

- Ingestão de dados CSV (camada Bronze)
- Padronização de tipos e timestamps
- Construção de candles OHLCV
- Cálculo de métricas analíticas (retorno, range, volatilidade)
- Criação de features
- Aplicação de clustering (KMeans)
- Geração das tabelas analíticas na camada Silver
- Base para agregações da camada Gold e dashboards

Este notebook é a **fonte primária de código** utilizada para obtenção dos
resultados descritos nos arquivos de análise do projeto.
