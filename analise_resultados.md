# Análise dos Resultados

## Visão Geral
A partir dos dados intraday do WINFUT processados no pipeline analítico,
foram geradas visualizações e análises com foco em volatilidade, retorno
e identificação de regimes de mercado ao longo do dia.

Os resultados a seguir respondem diretamente às perguntas de negócio
definidas no objetivo do MVP.

## Volatilidade por Faixa de Horário

A análise do dashboard de volatilidade indica que determinados horários
do pregão apresentam maior variabilidade de preços.

Observa-se concentração de maior volatilidade:
- No início do pregão
- Em períodos de sobreposição com mercados externos
- Próximo ao encerramento

Esses horários representam maior risco operacional,
mas também maior potencial de oportunidade.

## Retorno Médio por Faixa de Horário

Os resultados mostram que o retorno médio não é uniforme ao longo do dia.
Algumas faixas horárias apresentam retornos médios mais consistentes,
enquanto outras exibem maior dispersão.

Essa diferença sugere que o fator tempo intraday
é relevante para estratégias de trade baseadas em assimetria.

## Identificação de Clusters de Candles

O modelo de clustering (KMeans) permitiu agrupar candles com
características semelhantes de retorno e volatilidade.

Os clusters identificados representam diferentes regimes de mercado,
como:
- Baixa volatilidade e baixo retorno
- Alta volatilidade com retornos assimétricos
- Movimentos de transição

- ## Análise de Risco e Retorno por Regime

Cada cluster apresenta um perfil distinto de risco e retorno.
Regimes classificados como alta volatilidade tendem a apresentar
maior dispersão de retornos, enquanto regimes mais estáveis
exibem comportamento mais previsível.

Essa segmentação permite avaliar o risco de forma contextual,
não apenas por métricas globais.

## Apoio à Tomada de Decisão

Os padrões identificados podem apoiar decisões operacionais,
como:
- Seleção de horários mais favoráveis para operar
- Ajuste de risco conforme o regime de mercado
- Base analítica para desenvolvimento de estratégias futuras

## Análise de Risco e Retorno por Regime

A análise dos clusters evidencia que cada regime de mercado apresenta
um perfil distinto de risco e retorno.

Clusters associados à alta volatilidade tendem a apresentar maior
dispersão de retornos, enquanto regimes de baixa volatilidade exibem
comportamento mais estável e previsível.

Essa segmentação permite avaliar risco de forma contextual,
considerando o regime vigente, e não apenas métricas agregadas.

## Apoio à Tomada de Decisão

Os padrões identificados ao longo do MVP fornecem suporte direto
à tomada de decisão operacional e estratégica.

Entre as aplicações práticas destacam-se:
- Identificação de horários mais favoráveis para operação
- Ajuste de exposição ao risco conforme o regime de mercado
- Base analítica para desenvolvimento de estratégias quantitativas


## Conclusão

O MVP atingiu seu objetivo ao estruturar um pipeline analítico capaz de
explorar padrões de volatilidade, retorno e regimes de mercado no WINFUT.

Os resultados obtidos validam a relevância do fator intraday
e demonstram o potencial da abordagem para análises futuras
e evolução do modelo.






O MVP demonstra valor prático ao transformar dados brutos
em informação acionável.

