# 📌 Telecom X – Previsão de Churn de Clientes

## 🎯 Propósito da Análise
Este projeto tem como objetivo **analisar e prever a evasão de clientes (churn)** da empresa **Telecom X**.  
Com base nos dados disponibilizados, foram realizadas etapas de **ETL, análise exploratória, preparação para Machine Learning e modelagem preditiva**.  
O foco é identificar os principais fatores que levam clientes a cancelar seus serviços e propor modelos capazes de antecipar esse comportamento.


## ⚙️ Preparação dos Dados
### 🔹 1. Transformações aplicadas
- Codificação **One-Hot Encoding** para variáveis categóricas em modelos baseados em árvores.  
- Normalização de variáveis numéricas para algoritmos lineares.

### 🔹 2. Separação dos dados
- Treino (75%) e Teste (25%).  
- Utilizado `stratify` para manter a proporção de churners.

Principais insights:
- Clientes com **menor tempo de permanência (`tenure`)** apresentam maior propensão ao churn.  
- Contratos **mensais** possuem maior taxa de evasão em comparação a contratos anuais ou bienais.  
- O valor das faturas (`MonthlyCharges` e `TotalCharges`) está fortemente associado à evasão.  

Exemplo de visualização:  
![Distribuição de Churn por Contrato](visualizacoes/churn_por_contrato.png)

## 🤖 Modelagem

### 🔹 Modelos utilizados
- **Regressão Logística**  
- **Random Forest**  

### 🔹 Métricas avaliadas
- **Accuracy**  
- **Precision**  
- **Recall**  
- **F1-score**  
- **ROC AUC**
### 🔹 Comparação de Resultados

| Modelo               | Accuracy | Precision | Recall | F1-score | ROC AUC |
|-----------------------|----------|-----------|--------|----------|---------|
| Regressão Logística  | 0.74     | 0.50      | 0.81   | 0.62     | 0.84    |
| Random Forest        | 0.77     | 0.54      | 0.62   | 0.58     | 0.83    |

- **Regressão Logística** → melhor para detectar churners (**Recall alto**).  
- **Random Forest** → melhor equilíbrio geral (**Accuracy e Precisão maiores**).  

### 🔹 Variáveis mais influentes
- `tenure`  
- `TotalCharges`  
- `MonthlyCharges`  
- `Contract`  
- `InternetService`  

---

## 🚀 Como Executar

### 1. Instale as dependências
```bash
pip install pandas numpy matplotlib seaborn scikit-learn

### 2. Execute o notebook
```bash
jupyter notebook TelecomX_BR_2.ipynb

### 3. Utilize os dados processados
O arquivo TelecomX_Data_processed.csv já contém os dados limpos e preparados para os modelos.

##📌 Conclusão

- O tempo de permanência (tenure) é o fator mais determinante no churn.
- Contratos curtos e valores elevados de fatura aumentam significativamente a probabilidade de evasão.
- Recomendação estratégica:
-- Usar Regressão Logística quando o foco for reduzir ao máximo o churn (maximizando recall).
-- Usar Random Forest quando o objetivo for equilíbrio entre custo e acerto.
-- Sugere-se explorar modelos mais avançados como XGBoost ou LightGBM para potencial ganho de desempenho.
