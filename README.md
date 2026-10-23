# Detecção de Fraudes com Machine Learning

##  Problema
Este projeto aborda a detecção de transações fraudulentas.  
O maior desafio é o **desbalanceamento extremo**: a maioria das transações são legítimas e poucas são fraude.  
Por isso, métricas como **acurácia** não são suficientes — precisamos avaliar **recall, precisão e F1 da classe fraude**.

---

## ⚙️ Preparação dos dados
- Normalização de variáveis (`StandardScaler`) para regressão logística.  
- Criação de variáveis derivadas (ex.: `Amount_log`).  
- Separação em treino e teste (`train_test_split`).  
- Tratamento do desbalanceamento com `class_weight="balanced"` e `scale_pos_weight` no XGBoost.  

---

## 🤖 Comparação entre modelos
| Modelo                          | Precisão (fraude) | Recall (fraude) | F1 (fraude) |
|---------------------------------|------------------|-----------------|-------------|
| Logistic Regression (threshold=0.3) | 0.79 | 0.71 | 0.75 |
| Random Forest                   | 0.84 | 0.76 | 0.79 |
| XGBoost (tuned)                 | 0.94 | 0.78 | 0.85 |

O **XGBoost** apresentou o melhor equilíbrio, com recall alto e precisão superior.

---

## Limiar de decisão
- Ajustar o threshold da regressão logística de 0.5 para 0.3 aumentou o recall, mostrando como o limiar influencia diretamente o trade-off entre recall e precisão.  
- Essa técnica é essencial em cenários de fraude, onde **capturar mais casos** é prioridade, mesmo com alguns falsos positivos.

---

## Interpretação com SHAP
- O SHAP revelou que variáveis como **V4, V14, V12, V10** carregam padrões fortes associados à fraude.  
- Isso traz **transparência**: além de prever, o modelo mostra quais variáveis influenciam mais cada decisão.  

---

## Evidências
- Todas as saídas (classification reports, gráficos de importância, plots do SHAP) estão salvas no notebook.  
- Isso garante que o modelo roda e gera resultados reproduzíveis.  

---

## Como rodar
1. Clone este repositório.  
2. Abra o notebook no Google Colab ou Jupyter.  
3. Execute todas as células para reproduzir os resultados.  
