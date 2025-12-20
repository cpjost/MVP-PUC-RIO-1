# Identificação de Clusters de Candles
**Objetivo da Análise**

O objetivo desta etapa é identificar regimes distintos de comportamento do mercado intraday do contrato futuro de índice (WINFUT), a partir do agrupamento de candles com características semelhantes de retorno e volatilidade.

A técnica de clustering permite segmentar o mercado em contextos operacionais distintos, apoiando análises de risco, assimetria e tomada de decisão baseada em dados.

-------------------------------------------------------------------------------------------------------------------------------------------------
**Metodologia Utilizada**

**Dados de Entrada**

A análise foi realizada sobre a base da camada Silver, contendo candles intraday com as seguintes variáveis principais:

Retorno do candle

Range (máximo – mínimo)

Timeframe

Timestamp

Categoria de horário

Essas variáveis representam medidas diretas de movimento de preço e volatilidade, fundamentais para caracterização de regimes de mercado.

-----------------------------------------------------------------------------------------------------------------------------------------------

**Preparação das Features**

As etapas de preparação incluíram:

Seleção das variáveis numéricas relevantes

Montagem do vetor de features

Normalização das variáveis (quando aplicável)

Remoção de registros inválidos ou inconsistentes

Essa preparação garante que o algoritmo de clustering seja influenciado apenas por padrões estruturais dos dados, e não por escalas distintas entre variáveis.

-----------------------------------------------------------------------------------------------------------------------------------------------

**Algoritmo de Clustering**

Foi utilizado o algoritmo KMeans, com as seguintes configurações:

Número de clusters: k = 3

Inicialização com seed fixa para reprodutibilidade

Abordagem não supervisionada

Objetivo exploratório (sem finalidade preditiva direta)

O valor de k foi definido de forma exploratória, buscando um equilíbrio entre granularidade e interpretabilidade dos regimes identificados.

-----------------------------------------------------------------------------------------------------------------------------------------------


**Resultados Obtidos**

O clustering resultou na identificação de três grupos distintos de candles, cada um representando um regime intraday com características próprias.

De forma geral, os clusters podem ser interpretados como:

-----------------------------------------------------------------------------------------------------------------------------------------------


**Cluster 0 – Baixa Volatilidade**

Candles com baixo range médio

Retornos próximos de zero

Comportamento mais estável e previsível

Associado a períodos de menor atividade do mercado

-----------------------------------------------------------------------------------------------------------------------------------------------

**Cluster 1 – Volatilidade Moderada**

Range intermediário

Retornos mais distribuídos

Regime de transição entre estabilidade e movimentos direcionais

Frequente em períodos intermediários do pregão

----------------------------------------------------------------------------------------------------------------------------------------------

**Cluster 2 – Alta Volatilidade**

Maior range médio

Retornos mais assimétricos

Maior risco operacional

Maior potencial de oportunidade

Associado a abertura, eventos externos e encerramento do pregão

----------------------------------------------------------------------------------------------------------------------------------------------

**Análise de Risco e Retorno por Regime**

A segmentação por clusters evidencia que **o risco e o retorno não são homogêneos ao longo do dia**. Cada regime apresenta:

Diferente perfil de volatilidade

Diferente distribuição de retornos

Diferente adequação a estratégias operacionais

Essa abordagem permite avaliar risco **de forma contextual**, considerando o regime vigente, e não apenas métricas agregadas.

----------------------------------------------------------------------------------------------------------------------------------------------

**Relação com os Dashboards**

Os clusters identificados nesta etapa são utilizados diretamente nos dashboards analíticos, em especial:

Dashboard 03 – Clusters de Candles

Análises de retorno médio por cluster

Distribuição de candles por regime

Essas visualizações permitem explorar os regimes ao longo do tempo e por faixa de horário.

----------------------------------------------------------------------------------------------------------------------------------------------

**Limitações**

Número de clusters definido de forma exploratória

Análise baseada em dados históricos

Uso de um único ativo (WINFUT)

Ausência de validação externa dos clusters

Essas limitações são aceitáveis dentro do escopo de um MVP acadêmico.

----------------------------------------------------------------------------------------------------------------------------------------------

**Conclusão**

A aplicação de clustering permitiu identificar regimes intraday distintos no comportamento do WINFUT, fornecendo uma base analítica sólida para:

Análise de risco contextual

Avaliação de assimetria

Apoio a decisões estratégicas

Evolução futura para modelos quantitativos

Essa segmentação complementa as análises temporais e reforça o valor do pipeline analítico desenvolvido neste MVP.

----------------------------------------------------------------------------------------------------------------------------------------------

**Referência ao Código**

A implementação completa desta análise encontra-se no notebook:
https://github.com/cpjost/MVP-PUC-RIO-1/blob/main/src/notebooksmvp-winfut-databricks-pipeline.ipynb



