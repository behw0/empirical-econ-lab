# Previsão da Inflação (IPCA) no Brasil com Regressão Linear

## Descrição do Projeto

Este projeto tem como objetivo desenvolver um modelo de Regressão Linear para prever a variação mensal do IPCA (Índice Nacional de Preços ao Consumidor Amplo), o índice oficial de inflação do Brasil. O estudo utiliza os valores passados (lags) da própria série do IPCA como variáveis explicativas (features).

Este foi um exercício prático para aplicar os conceitos fundamentais de análise de séries temporais e machine learning, desde a coleta e tratamento dos dados até a avaliação do modelo.

## Objetivos

* Coletar e tratar a série histórica do IPCA mensal.
* Realizar uma análise exploratória dos dados para identificar padrões e características da inflação.
* Implementar a engenharia de features baseada em lags da série.
* Treinar um modelo de Regressão Linear.
* Avaliar o desempenho do modelo utilizando métricas de erro como MAE e RMSE.
* Documentar o processo e os aprendizados.

## Tecnologias e Bibliotecas Utilizadas

* **Linguagem:** Python 3
* **Bibliotecas Principais:**
    * `pandas` para manipulação e análise de dados.
    * `numpy` para operações numéricas.
    * `python-bcb` para acesso à API de séries temporais do Banco Central do Brasil.
    * `matplotlib` e `seaborn` para visualização de dados.
    * `scikit-learn` para a implementação do modelo de Regressão Linear e cálculo das métricas de avaliação.
* **Ambiente:** Google Colaboratory (ou Jupyter Notebook)

## Fonte dos Dados

Os dados históricos do IPCA (variação mensal, código da série: 433) foram obtidos diretamente do Sistema Gerenciador de Séries Temporais (SGS) do Banco Central do Brasil.
O período analisado foi de Janeiro de 2000 a Abril de 2025 (ou a data mais recente disponível no momento da coleta).

## Metodologia Resumida

1.  **Coleta de Dados:** Obtenção da série do IPCA via API do BCB.
2.  **Análise Exploratória (EDA):** Verificação da estrutura dos dados, estatísticas descritivas, visualização da série temporal e da distribuição dos valores.
3.  **Engenharia de Features:** Criação de 3 features de lag (IPCA dos 3 meses anteriores). Linhas com valores NaN resultantes da criação dos lags foram removidas.
4.  **Divisão dos Dados:** Separação cronológica dos dados em conjunto de treino (primeiros 277 meses após tratamento dos lags) e conjunto de teste (últimos 24 meses).
5.  **Modelagem:** Treinamento de um modelo de Regressão Linear (`LinearRegression` do `scikit-learn`) com os dados de treino.
6.  **Avaliação:** O modelo foi avaliado no conjunto de teste utilizando as métricas MAE (Erro Absoluto Médio) e RMSE (Raiz do Erro Quadrático Médio). Também foi feita uma análise visual das previsões versus os valores reais e dos resíduos do modelo.

## Resultados Principais

O modelo de Regressão Linear treinado com os 3 lags do IPCA obteve os seguintes resultados no conjunto de teste (24 meses):

* **MAE (Erro Absoluto Médio):** 0.2404 p.p.
* **RMSE (Raiz do Erro Quadrático Médio):** 0.3347 p.p.

*(Lembre-se de colocar aqui os seus valores exatos de MAE e RMSE que você obteve!)*

Uma análise mais detalhada dos resultados e das previsões pode ser encontrada no notebook Jupyter (`.ipynb`) deste repositório.

## Como Executar o Projeto

1.  Clone ou baixe este repositório.
2.  O projeto principal está no arquivo `ipca_inflation_forecast.ipynb` (ou o nome que você deu ao seu notebook).
3.  Abra o notebook em um ambiente compatível (Google Colab, Jupyter Notebook/Lab).
4.  Certifique-se de que as bibliotecas listadas na seção "Tecnologias e Bibliotecas Utilizadas" estão instaladas. A primeira célula do notebook (`!pip install python-bcb`) instala a biblioteca específica do BCB, se necessário.
5.  Execute as células do notebook em ordem.

## Conclusões e Próximos Passos

Este modelo inicial de Regressão Linear serviu como um bom aprendizado prático do fluxo de um projeto de previsão. Embora sua capacidade preditiva seja limitada pela simplicidade das features e do algoritmo, ele estabelece uma base para comparações futuras.

**Sugestões para trabalhos futuros e melhorias:**
* Incorporar variáveis macroeconômicas exógenas (ex: Taxa Selic, Câmbio, IBC-Br).
* Experimentar modelos mais sofisticados (ARIMA, SARIMA, Random Forest, XGBoost, LSTMs).
* Realizar uma análise de estacionariedade e aplicar transformações se necessário.
* Implementar validação cruzada específica para séries temporais.

## Autor

* Lucas Bernardo
* **LinkedIn:** [(https://www.linkedin.com/in/bertsmz/)]
