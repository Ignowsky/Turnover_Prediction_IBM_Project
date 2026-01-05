# 📉 Predição de Turnover com People Analytics (Recall 76%)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Lib](https://img.shields.io/badge/Lib-Scikit--Learn-orange)
![Status](https://img.shields.io/badge/Status-Concluído-green)

> **De Analista de DP para People Analytics:** Como transformei dados de RH em estratégia de retenção, utilizando Machine Learning para antecipar saídas voluntárias.

---

## 💼 O Problema de Negócio

O Turnover (rotatividade) voluntário é um dos maiores drenos de receita e capital intelectual de uma empresa. 
Neste projeto, atuei como **Cientista de Dados focado em RH**, com o objetivo de responder a três perguntas críticas:
1. **Quem** são os colaboradores com maior risco de sair?
2. **Por que** eles estão saindo?
3. **Como** podemos agir preventivamente?

Utilizei o dataset público **IBM HR Analytics** para simular um cenário real de predição.

---

## 🔍 Principais Insights (EDA)

Antes da modelagem, a Análise Exploratória de Dados (EDA) revelou padrões comportamentais cruciais:

### 1. O "Vilão" da Hora Extra
Muitos gestores acreditam que a saída é motivada apenas por salário. Os dados mostraram que o **Burnout** é um fator mais forte.
* Quem faz Hora Extra (`OverTime = Yes`) tem **3x mais chances** de pedir demissão do que quem cumpre o horário padrão.

### 2. O Risco Geracional (Gen Z)
* **Geração Z (< 24 anos):** Taxa de evasão de **43%**. Indica falha na atração ou onboarding.
* **Millennials (24-39 anos):** Maior volume absoluto de saídas. Representam a perda da força de trabalho técnica/produtiva.

---

## 🛠️ A Solução Técnica (Estratégia)

### A Batalha dos Modelos: Simplicidade > Complexidade
Inicialmente, testei algoritmos complexos como **XGBoost**. Porém, devido ao tamanho da base ("Small Data"), o modelo sofreu *Overfitting* (Recall de apenas 53%).

**A Decisão:** Optei por uma **Decision Tree (Árvore de Decisão)** otimizada.
* **Motivo:** Em RH, a *explicabilidade* (Explainability) é fundamental. Precisamos dizer ao gestor *por que* o funcionário está em risco. A Árvore oferece regras claras ("White Box").

### O "Pulo do Gato": Ajuste de Threshold
Um modelo padrão classifica risco acima de 50%. Para retenção de talentos, isso é arriscado (muitos falsos negativos).
* **Estratégia:** Ajustei a régua de sensibilidade (Threshold) para **30%**.
* **Resultado:** O **Recall subiu para 76%**.
* **Trade-off:** Aceitamos investigar mais "alarmes falsos" para garantir que nenhum talento crítico saia sem ser notado.

---

## 📊 Resultados Finais

O produto final não é o código, mas uma **Lista de Retenção Priorizada** entregue ao RH:

| Nível de Risco | Probabilidade | Ação Sugerida |
| :--- | :--- | :--- |
| **🔴 CRÍTICO** | > 70% | Intervenção Imediata (Revisão Salarial/Promoção) |
| **🟡 ALERTA** | > 30% | Conversa de Carreira e Feedback (PDI) |
| **🟢 BAIXO** | < 30% | Ações de Clima Organizacional |

**Métricas do Modelo (Test Set):**
* **Recall (Classe 1 - Saiu):** 76%
* **Feature Importance:** Tempo de Casa (30%), Idade (21%), Hora Extra (18%).

---

## 🚀 Como Executar o Projeto

### Pré-requisitos
* Python 3.x
* Pandas, Seaborn, Scikit-learn

### Instalação
```bash
# Clone este repositório
git clone [https://github.com/SEU-USUARIO/Turnover-Prediction-Project.git](https://github.com/SEU-USUARIO/Turnover-Prediction-Project.git)

# Instale as dependências
pip install pandas seaborn scikit-learn matplotlib
