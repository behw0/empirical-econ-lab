# Previsão da Inflação (IPCA) com Machine Learning no Brasil

![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)
![Libraries](https://img.shields.io/badge/Bibliotecas-Scikit--learn%20%7C%20Pandas%20%7C%20BCB-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## 🎯 Objetivo do Projeto

Este projeto demonstra um fluxo de trabalho completo de ciência de dados para prever a variação mensal do **IPCA (Índice Nacional de Preços ao Consumidor Amplo)**, o principal indicador de inflação do Brasil.

Partindo de um modelo simples, o projeto evolui de forma iterativa, incorporando mais dados e utilizando algoritmos mais sofisticados para aprimorar a precisão das previsões.

## 📊 Resumo dos Resultados

A principal conclusão do projeto é a eficácia de modelos não-lineares (como o Random Forest) em capturar as complexas relações das variáveis macroeconômicas. A tabela abaixo compara o desempenho dos três modelos desenvolvidos no mesmo conjunto de teste (últimos 24 meses).

| Modelo | Algoritmo | MAE (p.p.) ↓ | RMSE (p.p.) ↓ | Análise Breve |
| :--- | :--- | :---: | :---: | :--- |
| **Básico** | Regressão Linear | `0.2404` | `0.3347` | Um ponto de partida razoável usando apenas a própria inflação passada. |
| **Intermediário** | Regressão Linear | `0.2739` | `0.3534` | Piorou o desempenho, indicando que o modelo linear não conseguiu extrair valor da Selic e do Câmbio. |
| **Avançado (Otimizado)** | **Random Forest** | **`0.1262`** | **`0.1799`** | **Melhor modelo.** Redução de ~47% no MAE e ~46% no RMSE em relação ao modelo básico. |

*MAE = Erro Absoluto Médio; RMSE = Raiz do Erro Quadrático Médio. Valores menores são melhores.*

## 📈 Evolução dos Modelos

O projeto foi dividido em três etapas, cada uma contida em seu próprio notebook.

#### 1. Modelo Básico (`ipca_inflation_forecast_basic.ipynb`)
- **Descrição:** Um modelo autorregressivo simples que usa apenas os valores passados (lags) do próprio IPCA para fazer previsões.
- **Features:** 3 lags do IPCA.
- **Algoritmo:** `LinearRegression`.

#### 2. Modelo Intermediário (`ipca_inflation_forecast_intermediary.ipynb`)
- **Descrição:** Tentativa de aprimorar o modelo básico adicionando variáveis macroeconômicas exógenas.
- **Features:** Lags do IPCA (3), Taxa Selic (2) e Taxa de Câmbio (2).
- **Algoritmo:** `LinearRegression`.
- **Conclusão:** A adição de novas variáveis em um modelo linear simples não foi suficiente para melhorar a performance, indicando a necessidade de um algoritmo mais robusto.

#### 3. Modelo Avançado (`ipca_inflation_forecast_advanced.ipynb`)
- **Descrição:** Utiliza um modelo não-linear e técnicas mais avançadas de validação e otimização para extrair o máximo de informação das features.
- **Features:** As mesmas do modelo intermediário.
- **Algoritmo:** `RandomForestRegressor`.
- **Técnicas Chave:**
    - **Validação Cruzada:** `TimeSeriesSplit` para uma avaliação robusta em dados temporais.
    - **Otimização:** `GridSearchCV` para encontrar os melhores hiperparâmetros do modelo.
- **Resultado:** Desempenho significativamente superior, validando a abordagem. A análise de importância de features mostrou que o `IPCA_lag1` é a variável mais preditiva, seguida pela Taxa Selic.

## 🛠️ Tecnologias e Fontes de Dados

* **Linguagem:** Python 3
* **Bibliotecas:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn e `python-bcb`.
* **Fonte dos Dados:** As séries temporais foram obtidas diretamente do **Sistema Gerenciador de Séries Temporais (SGS)** do Banco Central do Brasil via API.
    * **IPCA:** Série 433
    * **Taxa Selic:** Série 11
    * **Taxa de Câmbio (USD/BRL):** Série 1


## 🔮 Próximos Passos e Melhorias

-   **Engenharia de Features:** Testar novas variáveis (preços de commodities, índices de atividade econômica, expectativas do Boletim Focus).
-   **Modelos Alternativos:** Experimentar outros algoritmos potentes como XGBoost, LightGBM ou modelos econométricos como SARIMAX.
-   **Análise de Resíduos:** Aprofundar a análise de erros para identificar padrões não capturados.
-   **Deploy:** Encapsular o melhor modelo em uma API simples usando Flask ou FastAPI para realizar previsões sob demanda.
