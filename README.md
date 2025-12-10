**WINFUT Intraday Quantitative Analysis (2019–2025)**
---------------------------------------------------------------------------------------------------------------------------------------------

**Visão Geral:**
---------------------------------------------------------------------------------------------------------------------------------------------

Este projeto é um MVP (Minimum Viable Product) desenvolvido como requisito para a pós-graduação em Ciência de Dados da PUC-Rio (Módulo: Engenharia de Dados).

O objetivo é construir um pipeline de dados completo (Coleta → Preparação → Modelagem → Carga → Análise) utilizando Databricks + PySpark + Delta Lake para analisar padrões intraday do contrato futuro do índice Ibovespa (WINFUT), incluindo:

1. Volatilidade intraday

2. Distribuição de retornos

3. Probabilidade de retorno positivo por hora

4. Regimes de volatilidade (K-Means)

5. Padrões por timeframe e dia da semana


**Objetivo do Projeto:**
---------------------------------------------------------------------------------------------------------------------------------------------

**O Problema:**
---------------------------------------------------------------------------------------------------------------------------------------------

O mercado intraday é altamente volátil, não linear, e sensível a microvariações.
Traders que observam apenas gráficos tradicionais (candlestick, renko, tape reading) não conseguem medir:

1. Horários de maior volatilidade

2. Períodos com maior probabilidade de retorno positivo

3. Distribuição estatística dos retornos

4. Regimes de volatilidade intraday

5. Comportamento por timeframe (5m, 15m, 60m)

6. Padrões semanais

O MVP resolve o problema de falta de visão estruturada e estatística, substituindo percepções subjetivas por informações quantitativas.

**Perguntas de Negócio:**
---------------------------------------------------------------------------------------------------------------------------------------------
Perguntas de Negócio (Business Questions)

O projeto busca responder:

**Tendência Intraday:**
Quais horários apresentam maior volatilidade média?

**Eficiência do Mercado:**
Qual a probabilidade de um candle fechar positivo ao longo do pregão?

**Distribuição Estatística:**
Como os retornos intraday se distribuem? São simétricos? Possuem caudas longas?

**Regimes de Volatilidade:**
O WINFUT se comporta de forma diferente em ambientes de baixa, média e alta volatilidade?

**Padrões por Timeframe e Semana:**
Existem diferenças significativas entre 5m, 15m e 60m?
Os dias da semana influenciam no range médio?

**Dados:**
---------------------------------------------------------------------------------------------------------------------------------------------

**Fonte**

Arquivos históricos de WINFUT provenientes de plataformas de mercado (profitchart pro)contendo:

**Preço de abertura, máximo, mínimo e fechamento**

**Volume**

**Quantidade**

**Timestamp**

**Formato**
---------------------------------------------------------------------------------------------------------------------------------------------

CSV → Bronze
Delta → Silver e Gold

**Arquitetura do Pipeline:**
---------------------------------------------------------------------------------------------------------------------------------------------

**Camada Bronze - Ingestão**
---------------------------------------------------------------------------------------------------------------------------------------------
| Campo      | Tipo   | Descrição              |
| ---------- | ------ | ---------------------- |
| ativo      | string | WINFUT                 |
| data       | string | Data do pregão         |
| hora       | string | Horário do candle      |
| abertura   | string | Preço de abertura      |
| maximo     | string | Preço máximo           |
| minimo     | string | Preço mínimo           |
| fechamento | string | Preço de fechamento    |
| volume     | string | Volume negociado       |
| quantidade | string | Quantidade de negócios |
| timeframe  | string | 5m, 15m, 60m           |


**Camada Silver - Trasformação**
---------------------------------------------------------------------------------------------------------------------------------------------
Transformações aplicadas:

1. Conversão numérica de preços

2. Padronização de tipos

3. Criação de timestamp unificado

4. Criação de range = max - min

5. Criação de retorno = (fechamento - abertura) / abertura

6. Criação de hora_num e dia_semana

7. Limpeza e normalização



**Camada Gold - Análises e Features**
---------------------------------------------------------------------------------------------------------------------------------------------
Indicadores derivados:

**Volatilidade**

1. Range_medio_por_hora

2. Range_medio_por_timeframe

3. Range_medio_por_dia_semana

**Retorno**

1. Prob_retorno_positivo

2. Retorno_medio_por_hora

3. Retorno_medio_por_timeframe

**Regimes de Mercado**

K-Means aplicado sobre:

1. Range

2. Volume

3. Volatilidade média

Regimes resultantes:

**Cluster 0 – Baixa volatilidade**

**Cluster 1 – Média volatilidade**

**Cluster 2 – Alta volatilidade**

**Catálogo de Dados – Tabela Silver**
---------------------------------------------------------------------------------------------------------------------------------------------
| Coluna     | Tipo      | Descrição                  |
| ---------- | --------- | -------------------------- |
| timestamp  | timestamp | Momento do candle          |
| abertura   | double    | Preço de abertura          |
| maximo     | double    | Preço máximo               |
| minimo     | double    | Preço mínimo               |
| fechamento | double    | Preço de fechamento        |
| range      | double    | Volatilidade do candle     |
| retorno    | double    | Variação percentual        |
| volume     | double    | Volume financeiro          |
| quantidade | double    | Numero de negocios         |
| timeframe  | string    | 5m, 15m, 60m               |
| hora       | int       | Hora extraída do timestamp |
| dia_semana | int       | Dia da semana (1–7)        |

**Dashboards**
---------------------------------------------------------------------------------------------------------------------------------------------
**Dashboard 1 — Volatilidade Intraday**

1. Range médio por hora

2. Range por timeframe

3. Range por dia da semana

4. Heatmap: hora × timeframe

**Dashboard 2 — Tendência e Retorno**

1. Probabilidade de retorno positivo

2. Distribuição dos retornos

3. Retorno médio por timeframe

4. Tendência horária

**Dashboard 3 — Regimes de Mercado**

1. Frequência por cluster

2. Range médio por cluster

3. Retorno médio por cluster

4. Heatmap cluster × hora

**Conclusões**
---------------------------------------------------------------------------------------------------------------------------------------------
**O mercado WINFUT possui padrões intraday bem definidos.
Período da manhã concentra maior volatilidade.
Distribuição dos retornos apresenta caudas longas.
K-Means revelou três regimes claros de volatilidade.
Probabilidade de retorno positivo não é uniforme ao longo do dia.**

