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

**Camada Bronze - Ingestão **
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


**Camada Silver - Trasformação **
---------------------------------------------------------------------------------------------------------------------------------------------
Transformações aplicadas:

1. Conversão numérica de preços

2. Padronização de tipos

3. Criação de timestamp unificado

4. Criação de range = max - min

5. Criação de retorno = (fechamento - abertura) / abertura

6. Criação de hora_num e dia_semana

7. Limpeza e normalização



**Camada Gold:**
---------------------------------------------------------------------------------------------------------------------------------------------

Volatilidade média por hora, timeframe e semana

Probabilidade de retorno positivo

Análises estatísticas

Tabelas agregadas para dashboards

**Dashboards Criados:**
---------------------------------------------------------------------------------------------------------------------------------------------

**Dashboard 1 — Volatilidade Intraday**
---------------------------------------------------------------------------------------------------------------------------------------------

Range médio por hora

Range médio por timeframe

Range por dia da semana

Heatmap hora × timeframe

**Dashboard 2 — Tendência e Retorno**
---------------------------------------------------------------------------------------------------------------------------------------------

Probabilidade de retorno positivo por hora

Histograma dos retornos

Retorno médio por timeframe

Boxplot por categoria de volatilidade

**Dashboard 3 — Regimes de Mercado**
---------------------------------------------------------------------------------------------------------------------------------------------

Frequência por cluster

Range médio por cluster

Probabilidade de retorno positivo por regime

Heatmap cluster × hora

Tecnologias Utilizadas

Databricks Community Edition

Apache Spark / PySpark

Delta Lake

Spark MLlib

Python 3.10

Databricks Dashboards

**Conclusões Principais**
---------------------------------------------------------------------------------------------------------------------------------------------

O WINFUT apresenta padrões claros de volatilidade intraday.

A probabilidade de retorno positivo varia significativamente por horário.

Clusters de alta volatilidade não garantem maiores retornos.

O pipeline permite análises repetíveis e escaláveis.





