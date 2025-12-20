# Catálogo de Dados

## Fonte de Dados
- Ativo: WINFUT (Contrato Futuro de Índice)
- Tipo: Dados intraday (candles)
- Origem: CSV histórico
- Frequência: Timeframes intraday (ex: 15 minutos)

---

## Camada Bronze – mvp_bronze

### Descrição
Dados brutos ingeridos a partir de arquivos CSV, com padronização inicial
de tipos e timestamps.

### Principais Colunas
| Coluna       | Tipo     | Descrição |
|--------------|----------|-----------|
| ativo        | string   | Identificador do ativo |
| data         | date     | Data do candle |
| hora         | string   | Hora do candle |
| abertura     | double   | Preço de abertura |
| maximo       | double   | Preço máximo |
| minimo       | double   | Preço mínimo |
| fechamento   | double   | Preço de fechamento |
| volume       | double   | Volume negociado |
| timestamp    | timestamp| Data e hora unificadas |

---

## Camada Silver – mvp_silver_fato_candle_regimes

### Descrição
Tabela fato com enriquecimento analítico dos candles.

### Colunas Derivadas
| Coluna          | Tipo     | Regra de Cálculo |
|-----------------|----------|------------------|
| range           | double   | maximo - minimo |
| retorno         | double   | (fechamento / abertura) - 1 |
| timeframe       | string   | Intervalo do candle |
| categoria_hora  | string   | Faixa horária categorizada |
| features        | vector   | Vetor para ML |
| cluster         | int      | Cluster KMeans |
| vol_categoria   | string   | Baixa / Média / Alta |

---

## Camada Gold – Agregações Analíticas

### Descrição
Tabelas agregadas para consumo analítico e dashboards.

### Métricas
- Volatilidade média
- Retorno médio
- Distribuição por cluster
- Probabilidade de retorno positivo
- Análise por faixa horária e timeframe

