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
