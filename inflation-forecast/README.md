# Previsão da Inflação (IPCA) no Brasil


## Versões do Modelo

### 1. Modelo Básico (`ipca_inflation_forecast_basic.ipynb`)
* **Features Utilizadas:** Apenas lags da própria série do IPCA (3 lags).
* **Período dos Dados:** Janeiro de 2000 a Abril de 2025.
* **Algoritmo:** Regressão Linear.
* **Resultados no Conjunto de Teste (24 meses):**
    * MAE: `0.2404` p.p.
    * RMSE: `0.3347` p.p.
* **Link para o Notebook:** [ipca_inflation_forecast_basic.ipynb](ipca_inflation_forecast_basic.ipynb)

### 2. Modelo Intermediário (`ipca_inflation_forecast_intermediary.ipynb`)
* **Features Utilizadas:** Lags do IPCA (3 lags), lags da Taxa Selic (2 lags da média mensal da taxa diária) e lags da Taxa de Câmbio (2 lags da média mensal USD/BRL).
* **Período dos Dados:** Janeiro de 2000 a Abril de 2025.
* **Algoritmo:** Regressão Linear.
* **Resultados no Conjunto de Teste (24 meses):**
    * MAE: `0.2739` p.p.
    * RMSE: `0.3534` p.p.
* **Análise:** A inclusão das features de Selic e Câmbio, neste modelo linear simples, resultou em uma pequena piora no desempenho.
* **Link para o Notebook:** [ipca_inflation_forecast_intermediary.ipynb](ipca_inflation_forecast_intermediary.ipynb)

### 3. Modelo Avançado (`ipca_inflation_forecast_advanced.ipynb`)
* **Features Utilizadas:** Lags do IPCA (3 lags), lags da Taxa Selic (2 lags da média mensal da taxa diária) e lags da Taxa de Câmbio (2 lags da média mensal USD/BRL) - mesmo conjunto do intermediário.
* **Período dos Dados:** Janeiro de 2000 a Abril de 2025.
* **Algoritmo:** Random Forest Regressor com hiperparâmetros otimizados via GridSearchCV e validação cruzada para séries temporais (TimeSeriesSplit).
* **Melhores Hiperparâmetros Encontrados:**
    * `max_depth`: `10`
    * `min_samples_leaf`: `2`
    * `min_samples_split`: `5`
    * `n_estimators`: `100`
* **Resultados no Conjunto de Teste Final (24 meses):**
    * MAE: `0.1262` p.p.
    * RMSE: `0.1799` p.p.
* **Análise:** O Random Forest otimizado apresentou uma melhora significativa no desempenho em relação aos modelos lineares, demonstrando a capacidade de um modelo não-linear em capturar relações mais complexas com as features macroeconômicas.
* **Link para o Notebook:** [ipca_inflation_forecast_advanced.ipynb](ipca_inflation_forecast_advanced.ipynb)

## Tecnologias e Bibliotecas Utilizadas
* **Linguagem:** Python 3
* **Bibliotecas Principais:** Pandas, NumPy, python-bcb, Matplotlib, Seaborn, Scikit-learn.
* **Ambiente:** Google Colaboratory.

## Fonte dos Dados
* IPCA (variação mensal, código 433): Sistema Gerenciador de Séries Temporais (SGS) do Banco Central do Brasil.
* Taxa Selic (diária efetiva, código 11): SGS/BCB.
* Taxa de Câmbio (PTAX venda, código 1): SGS/BCB.

## Como Executar os Projetos
1.  Navegue para o notebook desejado (básico ou intermediário).
2.  Abra-o em um ambiente compatível (Google Colab, Jupyter Notebook/Lab).
3.  Execute as células do notebook em ordem. A biblioteca `python-bcb` será instalada se necessário.

* **Refinamento do Modelo Avançado:**
    * Testar outras combinações de hiperparâmetros para o Random Forest.
    * Aplicar engenharia de features mais sofisticada (transformações para estacionariedade, padronização, novas variáveis como expectativas do Focus, etc.).
    * Analisar a importância das features do modelo otimizado para possível seleção.
* **Explorar Outros Modelos:** Testar algoritmos como XGBoost, LightGBM, ou modelos econométricos como SARIMAX ou Prophet.
* **Comparação Robusta:** Implementar um framework de backtesting mais completo.

## Autor
* Lucas Bernardo
* **LinkedIn:** https://www.linkedin.com/in/bertsmz/
