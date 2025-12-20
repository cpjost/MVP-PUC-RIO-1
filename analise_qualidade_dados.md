# Análise de Qualidade de Dados

## Visão Geral
Antes das análises e da aplicação de modelos de machine learning,
foi realizada uma avaliação da qualidade dos dados intraday do WINFUT
para garantir consistência, confiabilidade e aderência ao objetivo do MVP.

---

## Verificação de Valores Nulos
- Foi realizada a checagem de valores nulos nas colunas principais
  (abertura, fechamento, máximo, mínimo, volume).
- Não foram identificados nulos relevantes após a ingestão na camada Silver.
- Registros incompletos foram descartados na etapa de processamento.

---

## Verificação de Duplicidades
- Foi avaliada a existência de candles duplicados por timestamp.
- Duplicatas foram removidas para garantir unicidade temporal dos registros.

---

## Validação de Faixas de Valores
- Foram verificadas faixas válidas de preço (máximo ≥ mínimo).
- Registros com inconsistências lógicas foram filtrados.
- Volume zerado ou anômalo foi mantido apenas para análise exploratória,
  sem impacto direto no clustering.

---

## Outliers
- Foram identificados candles com ranges extremos.
- Os outliers não foram removidos automaticamente, pois representam
  eventos reais de alta volatilidade do mercado.
- Esses registros foram mantidos por serem relevantes para análise
  de regimes de mercado.

---

## Decisões de Qualidade
- Optou-se por preservar eventos extremos de mercado.
- O foco foi garantir consistência estrutural, não suavização dos dados.
- As decisões adotadas são compatíveis com análises financeiras intraday.

