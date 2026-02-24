# Departamento de RH — Análise de Rotatividade de Funcionários

## Descrição

Este projeto realiza uma análise exploratória de dados (EDA) sobre o dataset de RH da IBM, com foco na identificação dos principais fatores associados à rotatividade (attrition) de funcionários.

O notebook foi desenvolvido no Kaggle e utiliza Python com as principais bibliotecas de ciência de dados.

---

## Dataset

- **Fonte:** IBM HR Analytics Employee Attrition & Performance (Kaggle)
- **Registros:** 1.470 funcionários
- **Colunas:** 35 features originais (31 após remoção de colunas constantes)
- **Variável alvo:** `Attrition` (Yes / No)

### Distribuição da variável alvo

| Attrition | Quantidade | Percentual |
|-----------|-----------|------------|
| No        | 1.233      | ~84%       |
| Yes       | 237        | ~16%       |

---

## Estrutura do Notebook

1. **Importação de bibliotecas** — pandas, numpy, matplotlib, seaborn
2. **Carregamento e inspeção dos dados** — `shape`, `dtypes`, `describe()`, `isnull()`
3. **Limpeza dos dados** — remoção de colunas com variância zero (`EmployeeCount`, `Over18`, `StandardHours`)
4. **Análise Exploratória (EDA)**
   - Distribuição da variável alvo (Attrition)
   - Histogramas de variáveis numéricas
   - Comparação entre funcionários que saíram vs. permaneceram
   - Análise de variáveis categóricas (JobRole, Department, MaritalStatus, etc.)
5. **Insights e conclusões**

---

## Principais Insights

- A taxa de rotatividade é de aproximadamente **16%** (237 de 1.470 funcionários).
- Funcionários que saíram tendem a ter **menor satisfação no trabalho**, **menor tempo de empresa** e **menor nível salarial**.
- Variáveis como `OverTime`, `JobRole`, `MaritalStatus` e `DistanceFromHome` apresentam correlação com a saída de funcionários.
- Funcionários solteiros e com cargo de `Sales Representative` apresentam maior propensão ao desligamento.

---

## Machine Learning

### Objetivo

Com base nos padrões identificados na EDA, o próximo passo é construir modelos de classificação capazes de **prever a rotatividade de funcionários** (Attrition: Yes/No), auxiliando o RH na tomada de decisões preventivas.

---

### Pré-processamento para Modelagem

- **Encoding** de variáveis categóricas: `LabelEncoder` para binárias, `get_dummies` para nominais
- **Balanceamento de classes**: técnica SMOTE ou `class_weight='balanced'` (dado o desbalanceamento ~84%/16%)
- **Divisão treino/teste**: 80% treino, 20% teste (estratificado pela variável alvo)
- **Normalização**: `StandardScaler` aplicado nas features numéricas

---

### Modelos Utilizados

| Modelo | Descrição |
|---|---|
| **Regressão Logística** | Modelo base interpretável para classificação binária |
| **Random Forest** | Ensemble robusto, resistente a overfitting e com importância de features |

---

### Métricas de Avaliação

Devido ao desbalanceamento da variável alvo (~16% Yes), as métricas prioritárias são:

- **Recall (Sensibilidade)** — minimizar falsos negativos (funcionários que saem, mas não foram detectados)
- **F1-Score** — equilíbrio entre precisão e recall
- **ROC-AUC** — capacidade geral de discriminação do modelo
- **Matriz de Confusão** — visualização completa dos erros de classificação

---

### Importância das Features

As variáveis mais relevantes para a previsão de rotatividade, com base na EDA e nos modelos baseados em árvore:

1. `OverTime` — fazer horas extras aumenta significativamente o risco de saída
2. `MonthlyIncome` — salários menores estão correlacionados com maior rotatividade
3. `YearsAtCompany` — funcionários com menos tempo de empresa saem mais
4. `JobRole` — cargos como `Sales Representative` apresentam maior churn
5. `MaritalStatus` — solteiros têm maior propensão ao desligamento
6. `DistanceFromHome` — maior distância associada à maior rotatividade
7. `JobSatisfaction` — baixa satisfação é fator determinante
8. `Age` — funcionários mais jovens tendem a sair com mais frequência

---

### Resultados Esperados

> O objetivo é atingir um **F1-Score ≥ 0.70** e **ROC-AUC ≥ 0.80** para a classe minoritária (Yes), garantindo que o modelo seja útil para intervenções do departamento de RH.

---

## Como Reproduzir

```bash
# Clone o repositório
git clone https://github.com/GabriellCarvalho/Departamento_RH.git
cd Departamento_RH

# Instale as dependências
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn

# Execute o notebook
jupyter notebook departamento-de-rh.ipynb
```

---

## Tecnologias Utilizadas

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.x-lightgrey)
![Scikit-learn](https://img.shields.io/badge/ScikitLearn-1.x-orange)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)

---

## Autor

**Gabriel Carvalho**  
[GitHub](https://github.com/GabriellCarvalho) · [Kaggle](https://www.kaggle.com/gabriellcarvalho)

---

*Projeto desenvolvido para fins de estudo e portfólio em Ciência de Dados e Machine Learning.*
