# :credit_card: Análise comportamental de usuários de Cartão de Crédito - Clusterização com K-Means

[Link do Google Colab](https://colab.research.google.com/drive/16ocGMD6qJ1ykBMsaitxnAO8-9ikIXox_?usp=sharing)

**Dataset:** Informações sobre clientes de um banco relacionados aos gastos utilizando cartão de crédito.

**Fonte:** Kaggle - [Credit Card Dataset for Clustering](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata)

## Resumo

Neste projeto, serão feitas análises sobre caractéristicas relacionadas ao comportamento consumidor dos clientes de um banco no uso do cartão de crédito.

O usuários serão agrupados de acordo com seus padrões de comportamento.

## Tratamentos dos dados

Foram removidos campos não relacionados ao comportamento dos usuarios. 

Valores ausentes foram preenchidos por medianas, consideradas aproximações aceitáveis no contexto.

Haviam valores de amplitudes muito altas, enquanto outros variavam entre 0 e 1, portanto todo o dataset foi normalizado para facilitar futuras visualizações.

## Modelagem e Validação

* Os modelos foram construídos utilizando k-Means e variações na quantidade de clusters.

* As comparações foram feitas sobre o mesmo dataset, normalizado, e com três métricas de validação:
  * Coeficiente de Silhouette
  * Índice de Davies-Bouldin
  * Índice Calinski-Harabasz
  
* Nas três métricas, 6 clusters foi uma quantidade que apresentou os melhores resultados.

![Coeficiente de Silhouette](https://github.com/Tathy/Analise_comportamental_usuarios_cartao_de_credito/blob/main/img/Silhouette_plot.png?raw=true)

![Índice de Davies-Bouldin](https://github.com/Tathy/Analise_comportamental_usuarios_cartao_de_credito/blob/main/img/Davies-Bouldin_plot.png?raw=true)

![Índice Calinski-Harabasz](https://github.com/Tathy/Analise_comportamental_usuarios_cartao_de_credito/blob/main/img/Calinski-Harabasz_plot.png?raw=true)

* O modelo com 6 clusters passou por mais duas validações:
  * Comparação com um modelo semelhante, mas com dataset aleatório
  * Estabilidade, com o dataset dividido em 3 subconjuntos

:seedling:
