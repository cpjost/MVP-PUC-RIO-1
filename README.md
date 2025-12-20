**Análise Intraday do WINFUT com Pipeline Analítico e Clustering**
---------------------------------------------------------------------------------------------------------------------------------------------

**Visão Geral**
---------------------------------------------------------------------------------------------------------------------------------------------

Este repositório contém o MVP (Minimum Viable Product) desenvolvido no contexto acadêmico da PUC-Rio, com foco na aplicação prática de conceitos de engenharia de dados, analytics e machine learning para análise de dados intraday do contrato futuro de índice (WINFUT).

O projeto estrutura um pipeline de dados em nuvem, organiza as informações em camadas analíticas e aplica técnicas de clustering para identificar regimes de mercado, padrões de volatilidade e retorno ao longo do pregão.


**Objetivo do MVP**
---------------------------------------------------------------------------------------------------------------------------------------------
O objetivo principal do MVP é:

Analisar dados intraday do WINFUT

Identificar padrões de volatilidade e retorno ao longo do dia

Detectar regimes de mercado por meio de clustering de candles

Apoiar decisões analíticas e operacionais com base em dados

O detalhamento completo do objetivo encontra-se em:

(objetivo_mvp.md)

**Perguntas de Negócio**
---------------------------------------------------------------------------------------------------------------------------------------------

O MVP busca responder às seguintes questões:

Quais horários do dia apresentam maior volatilidade média?

Existe diferença significativa de retorno médio entre faixas de horário?

É possível identificar clusters de candles com comportamentos semelhantes?

Esses clusters representam regimes distintos de risco e retorno?

Como esses padrões podem apoiar decisões estratégicas e operacionais

**Arquitetura da Solução**
---------------------------------------------------------------------------------------------------------------------------------------------
A solução foi estruturada seguindo o padrão Medallion Architecture, com as camadas:

Bronze – Ingestão de dados brutos

Silver – Dados tratados, enriquecidos e modelados

Gold – Agregações analíticas e consumo

Diagramas detalhados da arquitetura e pipelines podem ser encontrados na pasta:

assets/

**Camadas do Pipeline**
---------------------------------------------------------------------------------------------------------------------------------------------
 Camada Bronze (mvp_bronze)

Ingestão de dados via arquivos CSV históricos

Padronização inicial de tipos e timestamps

Persistência em formato analítico (Delta)

 Camada Silver

Construção de candles OHLCV

Cálculo de métricas como retorno e range

Criação de features analíticas

Categorização por faixa de horário

Aplicação de clustering (KMeans)

 Camada Gold

Agregações por horário, dia e regime

Base analítica para dashboards

Suporte à análise exploratória e estratégica

---------------------------------------------------------------------------------------------------------------------------------------------

**Catálogo de Dados**
---------------------------------------------------------------------------------------------------------------------------------------------

A descrição detalhada das tabelas, colunas e tipos de dados está documentada em:

 catalogo_dados.md
 
---------------------------------------------------------------------------------------------------------------------------------------------

**Qualidade dos Dados**
---------------------------------------------------------------------------------------------------------------------------------------------

Foram realizadas verificações de qualidade incluindo:

Checagem de valores nulos

Remoção de duplicidades

Validação de faixas lógicas de preços

Análise e tratamento de outliers

Os detalhes encontram-se em:

 analise_qualidade_dados.md
 
---------------------------------------------------------------------------------------------------------------------------------------------

**Análise dos Resultados**
---------------------------------------------------------------------------------------------------------------------------------------------

As análises realizadas permitiram:

Identificar horários com maior volatilidade intraday

Avaliar diferenças de retorno médio ao longo do dia

Detectar clusters de candles representando diferentes regimes de mercado

Os resultados e interpretações estão descritos em:

 analise_resultados.md

 identificação_de_clusters_de_candles.md
 
---------------------------------------------------------------------------------------------------------------------------------------------

**Modelagem Analítica**
---------------------------------------------------------------------------------------------------------------------------------------------

Técnica utilizada: KMeans

Variáveis baseadas em retorno e volatilidade

Abordagem exploratória, focada em segmentação de comportamento

Sem objetivo preditivo operacional neste MVP

---------------------------------------------------------------------------------------------------------------------------------------------

**Limitações**
---------------------------------------------------------------------------------------------------------------------------------------------


Uso de um único ativo (WINFUT)

Análise baseada em dados históricos

Modelo exploratório sem otimização extensiva

Ausência de backtesting de estratégias

Essas limitações são compatíveis com o escopo de um MVP acadêmico.

---------------------------------------------------------------------------------------------------------------------------------------------

**Próximos Passos**
---------------------------------------------------------------------------------------------------------------------------------------------


Como evoluções futuras, o projeto pode incorporar:

Dados em tempo real

Múltiplos ativos e timeframes

Modelos de machine learning mais avançados

Integração com estratégias quantitativas

Dashboards interativos em produção

---------------------------------------------------------------------------------------------------------------------------------------------

**Considerações Finais**
---------------------------------------------------------------------------------------------------------------------------------------------


Este MVP demonstra a aplicação prática de conceitos de dados e analytics
na análise de mercados financeiros, servindo como base tanto acadêmica
quanto para evolução em projetos profissionais e quantitativos.

---------------------------------------------------------------------------------------------------------------------------------------------
**Autor**
---------------------------------------------------------------------------------------------------------------------------------------------


Carlos Peter Jost
Projeto acadêmico – PUC-Rio

---------------------------------------------------------------------------------------------------------------------------------------------
## Licença
Este projeto está licenciado sob a licença MIT. Consulte o arquivo [LICENSE](LICENSE.md) para mais detalhes.


