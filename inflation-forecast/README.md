# Previsão da Inflação (IPCA) no Brasil

## Descrição do Projeto

Este projeto explora a construção de modelos para prever a variação mensal do IPCA (Índice Nacional de Preços ao Consumidor Amplo), o índice oficial de inflação do Brasil. Foram desenvolvidas diferentes versões do modelo, começando com uma abordagem simples e progredindo para a inclusão de variáveis macroeconômicas exógenas.

## Objetivos
* Coletar e tratar séries históricas relevantes (IPCA, Selic, Câmbio).
* Realizar análises exploratórias dos dados.
* Implementar engenharia de features, incluindo lags.
* Treinar e avaliar modelos de Regressão Linear.
* Comparar o desempenho dos modelos.
* Documentar o processo e os aprendizados.

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
* **Período dos Dados:** Janeiro de 2000 a Abril de 2025 (para IPCA) e dados correspondentes para Selic e Câmbio.
* **Algoritmo:** Regressão Linear.
* **Resultados no Conjunto de Teste (24 meses):**
    * MAE: `0.2739` p.p.
    * RMSE: `0.3534` p.p.
* **Análise:** A inclusão das features de Selic e Câmbio, neste modelo linear simples, resultou em uma pequena piora no desempenho em comparação com o modelo básico. Isso sugere que a relação dessas variáveis com o IPCA pode ser mais complexa e não-linear, ou que a especificação dos lags e o tratamento das variáveis precisam ser refinados.
* **Link para o Notebook:** [ipca_inflation_forecast_intermediary.ipynb](ipca_inflation_forecast_intermediary.ipynb)

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

## Próximos Passos e Trabalhos Futuros (para versões avançadas)
* Testar modelos mais sofisticados (Random Forest, XGBoost, SARIMA).
* Refinar a engenharia de features (diferentes lags, transformações, mais variáveis).
* Implementar validação cruzada para séries temporais.

## Autor
* Lucas Bernardo
* **LinkedIn:** https://www.linkedin.com/in/bertsmz/
