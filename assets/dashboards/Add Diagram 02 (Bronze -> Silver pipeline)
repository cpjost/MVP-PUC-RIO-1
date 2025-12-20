flowchart LR

A[Fonte de Dados<br/>WINFUT - Dados Intraday<br/>CSV e Histórico] --> B

B[Bronze<br/>mvp_bronze<br/><br/>• Upload CSV (DBFS)<br/>• Leitura Spark<br/>• Tipagem colunas<br/>• Padronização data/hora<br/>• Persistência Delta] --> C

C[Silver - Tabela Fato<br/>mvp.silver_fato_candle_regimes<br/><br/>• Candle (OHLCV)<br/>• range = maximo - minimo<br/>• retorno = (fechamento/abertura) - 1<br/>• timestamp (data + hora)<br/>• timeframe (ex: 15m)<br/>• categoria_hora (faixas)] --> D

D[Silver - Features<br/><br/>• Seleção de variáveis<br/>• Montagem de vetor features<br/>• Normalização (se aplicada)<br/>• Validação de nulos/outliers] --> E

E[Silver - Clustering<br/><br/>• Treino KMeans<br/>• prediction -> cluster<br/>• vol_categoria (ex: baixa/média/alta)<br/>• Persistência na fato] --> F

F[Saída para Camada Gold<br/><br/>• Agregações por hora/dia/timeframe<br/>• Métricas para dashboards] 
