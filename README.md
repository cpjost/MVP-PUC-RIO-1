**WINFUT Intraday Quantitative Analysis — Historical Intraday Samples**
---------------------------------------------------------------------------------------------------------------------------------------------

**Visão Geral:**
---------------------------------------------------------------------------------------------------------------------------------------------

Este projeto consiste em um MVP (Minimum Viable Product) desenvolvido como requisito para a Pós-Graduação em Ciência de Dados da PUC-Rio, no módulo de Engenharia de Dados.

O objetivo é construir um pipeline de dados completo — desde a ingestão até a análise — utilizando Databricks, PySpark e Delta Lake, com foco na análise quantitativa intraday do contrato futuro do índice Ibovespa (WINFUT).

O projeto investiga padrões estatísticos e comportamentais do mercado intraday, incluindo:

1. Volatilidade intraday

2. Distribuição de retornos

3. Probabilidade de retorno positivo por hora

4. Regimes de volatilidade via K-Means

5. Padrões por timeframe e dia da semana


**Objetivo do Projeto:**
---------------------------------------------------------------------------------------------------------------------------------------------

**O Problema:**
---------------------------------------------------------------------------------------------------------------------------------------------

O mercado intraday é caracterizado por alta volatilidade, não linearidade e comportamento estocástico. Traders e analistas que utilizam apenas ferramentas gráficas tradicionais — como candlestick, Renko ou tape reading — enfrentam dificuldades para mensurar, de forma objetiva, padrões estatísticos relevantes, tais como:

1. Horários de maior volatilidade

2. Probabilidade de retornos positivos ao longo do pregão

3. Distribuição estatística dos retornos intraday

4. Mudanças de regime de volatilidade

5. Diferenças comportamentais entre timeframes (5m, 15m, 60m)

6. Padrões semanais recorrentes

Este MVP resolve a falta de uma visão estatística estruturada do mercado intraday, substituindo percepções subjetivas por evidências quantitativas baseadas em dados.

**Perguntas de Negócio:**
---------------------------------------------------------------------------------------------------------------------------------------------

O projeto busca responder às seguintes questões:

**Tendência Intraday:**
Quais horários apresentam maior volatilidade média ao longo do pregão?

**Eficiência do Mercado:**
Qual a probabilidade de um candle intraday fechar positivo?

**Distribuição Estatística:**
Como os retornos intraday se distribuem?
Eles apresentam simetria ou caudas longas (fat tails)?

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

**Volume negociado**

**Quantidade de negócios**

**Timestamp do candle**

**Formato**
---------------------------------------------------------------------------------------------------------------------------------------------

CSV → Camada Bronze
Delta Lake → Silver e Gold

**Arquitetura do Pipeline:**
---------------------------------------------------------------------------------------------------------------------------------------------

**Camada Bronze - Ingestão**
---------------------------------------------------------------------------------------------------------------------------------------------
Dados brutos ingeridos diretamente dos arquivos CSV, sem tratamento analítico.
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
Aplicação de limpeza, padronização e criação de features básicas:

1. Conversão numérica de preços e volumes.

2. Padronização de tipos de dados

3. Criação de timestamp unificado

4. Cálculo de range = maximo − minimo

5. Cálculo de retorno = (fechamento − abertura) / abertura

6. Extração de hora e dia_semana

7. Tratamento de valores inconsistentes



**Camada Gold - Análises e Features**
---------------------------------------------------------------------------------------------------------------------------------------------
Camada analítica com agregações e métricas derivadas.

**Volatilidade**

1. Range médio por hora

2. Range médio por timeframe

3. Range médio por dia da semana

**Retorno**

1. Probabilidade de retorno positivo

2. Retorno médio por hora

3. Retorno médio por timeframe

**Regimes de Mercado**

K-Means aplicado sobre:

1. Range

2. Volume

3. Volatilidade média

Regimes identificados:

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
A distribuição dos retornos apresenta caudas longas, indicando risco assimétrico.
O algoritmo K-Means identificou três regimes claros de volatilidade.
A probabilidade de retorno positivo não é uniforme ao longo do pregão.**

