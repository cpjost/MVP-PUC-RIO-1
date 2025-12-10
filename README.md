**WINFUT Intraday Quantitative Analysis (2019–2025)**
---------------------------------------------------------------------------------------------------------------------------------------------

**Visão Geral:**
---------------------------------------------------------------------------------------------------------------------------------------------

Este projeto é um MVP (Minimum Viable Product) desenvolvido como requisito para a pós-graduação em Ciência de Dados da PUC-Rio (Módulo: Engenharia de Dados).

O objetivo é construir um pipeline de dados completo (Coleta, Preparação, Modelagem, Carga e Análise) em ambiente Cloud utilizando Databricks + Delta Lake para analisar padrões intraday do contrato futuro do índice Ibovespa (WINFUT), incluindo volatilidade, retorno, regimes de mercado (K-Means) e indicadores quantitativos.


**Objetivo do Projeto:**
---------------------------------------------------------------------------------------------------------------------------------------------

**O Problema:**
---------------------------------------------------------------------------------------------------------------------------------------------

O mercado intraday é altamente volátil e não linear. Traders e analistas, ao observarem apenas gráficos tradicionais, não conseguem mensurar padrões estatísticos importantes, como:

horários de maior volatilidade

distribuição de retornos intraday

probabilidade de retorno positivo por faixa horária

mudanças de regime de volatilidade

comportamento por timeframe e dia da semana

O problema central que este projeto resolve é a falta de uma visão estruturada e estatística do mercado intraday, substituindo percepções subjetivas por dados concretos.

**Perguntas de Negócio:**
---------------------------------------------------------------------------------------------------------------------------------------------

O MVP responde às seguintes questões principais:

Volatilidade Intraday
Quais são os horários, dias da semana e timeframes com maior volatilidade média?

Retorno e Tendência
Qual é a probabilidade de um candle fechar positivo por hora, timeframe e período do pregão?

Distribuição Estatística
Como se comporta a distribuição dos retornos intraday? É simétrica? Possui caudas longas?

Regimes de Mercado (K-Means)
Existem regimes distintos de volatilidade? Como influenciam no retorno?

Padrões Intraday
Existem janelas de maior eficiência considerando volatilidade × retorno?

**Dados:**
---------------------------------------------------------------------------------------------------------------------------------------------

Fonte: Arquivos CSV do WINFUT em múltiplos timeframes, exportado pelo programa profitchart da nelogica.
Formato: CSV
Timeframes: 5m, 15m, 60m

Campos Originais:

ativo

data

hora

abertura

máximo

mínimo

fechamento

volume

quantidade

Campos Criados (Silver / Gold)

timestamp

range (máximo − mínimo)

retorno

categoria_hora (manhã, almoço, tarde)

vol_categoria (baixa, média, alta – via K-Means)

**Arquitetura do Pipeline:**
---------------------------------------------------------------------------------------------------------------------------------------------

**Camada Bronze:**
---------------------------------------------------------------------------------------------------------------------------------------------

Leitura dos CSVs brutos

Padronização das colunas

União dos timeframes

**Camada Silver:**
---------------------------------------------------------------------------------------------------------------------------------------------

Conversão de tipos

Parse de vírgula/ponto

Criação de:

range

retorno

timestamp

categoria_hora

Escrita da tabela Delta mpv.silver_fato_candle

Silver + ML (Regimes)

Clusterização K-Means (k=3)

Identificação dos regimes de volatilidade

Nova tabela criada: mpv.silver_fato_candle_regimes

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





