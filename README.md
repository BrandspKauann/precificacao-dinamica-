# Precificação Dinâmica – Inteligência Artificial  
**Maximizando receita sem adivinhação: modelo XGBoost em produção.**

---

## Objetivo
Recomendar, dia a dia, o **preço que mais gera receita** (`price × demanda`) usando machine learning em dados de demanda, sazonalidade, eventos e concorrência.

---

## Dados
- **Base gerada**: 2 anos diários (2022-2023)  
- **Features**: price, competitor_price, season, event, demand (target)  
- **Sinais criados**: price_ratio, price_season, price_event, lag1_demand, dias do ano, semana

---

## Modelagem
- Algoritmo: **XGBoost** com validação temporal  
- Target: `log(demand+1)` para tratar elasticidade não-linear  
- Otimização de hiper-parâmetros com **Optuna** (40 trials)  
- Performance final: **MAE ≈ 10 unidades | R² ≈ 0,75**

---

## Resultados-chave
| Métrica | Valor |
|---------|-------|
| Erro médio absoluto | 10,2 unidades |
| R² | 0,75 |
| **Preço ótimo próximos 7 dias** | **R$ 150** (vs R$ 112-119 atual) |
| **Receita extra estimada** | **+R$ 8 mil/dia** |

---

## Importância das variáveis (top 5)
1. price_event  
2. event_black  
3. season_alta  
4. price  
5. price_ratio  

---

## Deploy & Próximos Passos
- API REST com FastAPI (`/predict` → demanda + preço ótimo)  
- Container Docker & pipeline Airflow para retreino diário  
- Teste A/B 50/50 para validar lift real  
- Monitoramento de drift e performance em Prometheus + Grafana  

---

## Tecnologias
`Python` | `pandas` | `XGBoost` | `Optuna` | `FastAPI` | `Docker` | `Apache Airflow`

---
**Star ⭐ se o preço ótimo te fez subir o ticket médio.**
