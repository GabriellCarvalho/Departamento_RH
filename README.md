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
