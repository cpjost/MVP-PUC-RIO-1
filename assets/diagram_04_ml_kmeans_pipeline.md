
flowchart LR

A[Silver - Base de Candles<br/>mvp.silver_fato_candle_regimes<br/>OHLCV + retorno + range + timestamp] --> B[Preparacao de Features<br/>Selecao de variaveis<br/>Tratamento de nulos/outliers<br/>Padronizacao opcional]

B --> C[Feature Engineering<br/>VectorAssembler -> features<br/>Opcional: StandardScaler -> scaled_features]

C --> D[Treino KMeans<br/>k (ex: 3)<br/>seed fixo<br/>fit(features)]

D --> E[Predicao<br/>transform -> prediction<br/>prediction -> cluster]

E --> F[Persistencia em Silver<br/>mvp.silver_fato_candle_regimes<br/>Adicionar colunas: cluster, vol_categoria]

F --> G[Consumo Analitico<br/>Agregacoes para Gold<br/>Dashboards 03 - Clusters]
