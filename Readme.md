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
  
## Análises descritivas das features por cluster

* O dataset tratado possui 16 colunas, o que torna difícil a visualização dos tributos separados por cluster. A visualização par a par também é dificultada pela quantidade de gráficos gerados.

* Foram analisadas as features mais representativas. 
	* Os atributos mais significativos serão os que determinarem maiores mudanças de valores, ou seja, os atributos com centroides mais dispersos.
	* Para encontrar estes atributos, foi medida a variância dentro de cada feature/eixo.
	* Os atributos considerados mais representativos e relacionados ao comportamento consumidor dos clientes foram: BALANCE, PURCHASES, CASH_ADVANCE, CREDIT_LIMIT e PAYMENTS.
	
* Cada cluster foi interpretado de acordo com a média que as features mais representativas possuíam.
	* Foi usado um atributo que não possuía muita representatividade (PRC_FULL_PAYMENT) pra ajudar na interpretação da relação entre outros dois atributos (PAYMENTS e BALANCE).
	* Após a análise por atributos, foi possível atribuir características marcantes de cada grupo de clientes. Ou seja, clientes de determinado cluster tendem a ter comportamentos parecidos.
	* Estas características podem ser usadas para formular possíveis regras de negócio que podem ser avaliadas, rejeitadas ou aceitas, utilizando Testes A/B.
	
## Descrições dos clientes por cluster

* A ordem dos clusters pode mudar na reexecução do código, mas as métricas tendem a se manter.

### Cluster 0
Clientes que gastam muito e são os piores pagadores. Cerca de 20%. Semelhante ao cluster 4, mas preferem efetuar compras direto no cartão.

### Cluster 1
Clientes que gastam mais e são os melhores pagadores. Cerca de 16%.

### Cluster 2
Clientes que preferem gastar através de saques e são pagadores medianos. Cerca de 11%.

### Cluster 3
Clientes que gastam pouco e são bons pagadores. Maior grupo de clientes, cerca de 35%.

### Cluster 4
Clientes que gastam muito em saques e são maus pagadores. Cerca de 12%. Semelhante ao cluster 0, mas preferem gastar usando dinheiro.

### Cluster 5
Clientes que não se encaixaram em picos, têm o menor limite de crédito e não são bons pagadores. É o menor grupo de clientes, cerca de 4%.

##

* Uma ação direcionada ao grupo 3 atingiria a maior quantidade de clientes, por ser o cluster mais numeroso. Esses clientes são bons pagadores, o que é bom para o banco, mas gastam pouco. Seria interessante encontrar uma forma desse clientes gastarem mais utilizando este cartão, incentivando eles a receber seus salários diretamente neste banco ou oferecendo algum plano de fidelização, por exemplo.

* Esta mesma estratégia pode ser aplicada ao grupo 1, pois clientes mais consumistas são mais lucrativos.

* Estas estratégias podem ser avaliadas através de Testes A/B, com os grupos sendo divididos aleatoriamente em teste e controle, por um determinado tempo. Caso haja um aumento relevante no lucro da empresa, a estratégia de negócio pode ser aplicada a todos os clientes pertencentes a estes perfis.
	
	
## Referências

Este projeto foi feito com o apoio de um curso da Alura, [Clustering: extraindo padrões de dados](https://cursos.alura.com.br/course/cluster-analysis).
