# E-Commerce-Identificar-os-perfis-dos-consumidores
Este projeto visa realizar uma segmentação completa dos usuários de um e-commerce com base em seu histórico de compras a fim de ajudar a equipe de marketing a desenvolver ofertas mais personalizadas para diferentes usuários.

Foi realizado:  
- Limpeza, padronização e exploração dos dados;  
- Análise RFM dos dados dos clientes;  
- Clusterização dos dados com base no modelo de K-means de ML;
- Formulação de testes estatísticos para testar as diferenças entre os clusters; 
- Conclusões e recomendações sobre como melhorar o serviço de clientes:  

## Índice

- [Metodologia](#metodologia)
- [Bibliotecas Utilizadas](#bibliotecas-utilizadas)
- [Conclusões](#conclusões)
- [Como Utilizar](#como-utilizar-este-repositório)
- [Possíveis Melhorias](#possíveis-melhorias)

## Metodologia
### Carregamento e Preparação dos Dados

1. **Carregamento dos Dados**:
    - Registros das compras realizadas: `/datasets/ecommerce_dataset_us.csv`

2. **Análise Exploratória dos Dados - EDA**:
    - Nesta etapa, realizamos uma boa limpeza dos dados para aproveitar somente as compras válidas dos clientes: removemos dados duplicados e dados ausentes; abatemos as compras canceladas/devolvidas e corrigimos descrições de produtos incoerentes/incorretas.
    - Realizamos um tratamento dos dados atípicos e ajustamos os tipos de dados.
    - Criamos plots para visualizar as métricas como quantidades e valores médios dos pedidos.

3. **Segmentação dos Clientes**

Utilizamos a Análise RFM para segmentar os clientes com base na Recência (tempo passado desde a última compra), Frequência (frequência em que os usuários realizam a compra) e Monetariedade (valor das compras realizadas pelo cliente). Após calcular os dados por cada cliente, padronizamos as métricas e aplicamos um modelo de Machine Learning para identificar o número ótimo de clusters. Por fim, classificamos esses clientes com base nas três métricas e geramos visualizações dos dados de volume dos pedidos e valores médios, dividido por cluster.

4. **Testando as Diferenças entre os Clusters**

Neste tópico, testamos as seguintes hipóteses, para avaliar a diferença entre os clusters:
- Teste 1: Testar a hipótese de que há diferença significativa no valor monetário das compras entre os grupos; 
- Teste 2: Testar a hipótese de que há diferença significativa na frequência de compra dos grupos;
- Teste 3: Testar a hipótese de que há diferença significativa na recencia entre os grupos.

Primeiro, aplicamos um teste de normalidade para definir se iríamos utilizar, ou não, um teste paramético, depois realizamos o teste estatístico e depois a análise pós HOC para identificar exatamente quais grupos diferiam entre si.  


## Bibliotecas Utilizadas

As seguintes bibliotecas Python foram utilizadas para a análise de dados e visualização:

- [Pandas](https://pandas.pydata.org/)
- [os-sys](https://docs.python.org/3/library/os.html)
- [Pathlib](https://docs.python.org/3/library/pathlib.html)
- [Plotly](https://plotly.com/)
- [Seaborn](https://seaborn.pydata.org/)
- [Matplotlib](https://matplotlib.org/)
- [Numpy](https://numpy.org/)
- [Scipy](https://scipy.org/)
- [Statsmodels](https://www.statsmodels.org/)
- [Scikit-learn](https://scikit-learn.org/)
- [Inflection](https://inflection.readthedocs.io/)
- [SQLAlchemy](https://www.sqlalchemy.org/)


## Conclusões

#### Segmentação dos clientes  
Após realizar as analises comentadas anteriormente, os clientes foram segmentados em 4 clusters:
- Cluster 3 - Clientes Fiéis: Compram recentemente. Compram com frequência. Gastam mais. 
- Cluster 0 - Promissor: Compradores recentes, mas não gastaram muito.
- Cluster 1 - Em risco:	Gastaram muito dinheiro e compraram com freqüência. Mas há muito tempo.
- Cluster 2 - Hibernando: A última compra foi feita a algum tempo. Pouco gasto e baixo número de pedidos.  
  
#### Testes estatísticos para comprovar as diferenças entre os clusters  
O resultado final foi muito semelhante ao que já havíamos visualizado anteriormente no gráfico de caixa por cluster: houve uma diferença estatisticamente significativa em todas as combinações de clusters no critério de recência, enquanto que na frequência e monetariedade houve diferença significativa em todos os clusters com exceção apenas entre os clusters 0 (cliente promissor) e 2 (cliente hibernando).

#### Recomendações à equipe de marketing  
A partir dos resultados, é possível identificar que a equipe de marketing deve seguir as seguintes estratégias:
- Clientes Fiéis: Esses são os clientes mais valiosos da empresa, devemos investir pra que fidelizemos eles de forma que se sintam mais dispostos a manter uma relação próxima da empresa, e continuem comprando com frequência e altos valores.
- Clientes Promissores: Investir em campanhas de marketing que induzam os clientes a continuar comprando, e ao mesmo tempo, passar a gastar mais por compra, até que eles se tornem Clientes Fiéis.
- Clientes Em risco: Realizar pesquisas para identificar o motivo pelo qual esses clientes pararam de comprar e enviar campanhas personalizadas para reavivar o interesse do clientes em comprar com a empresa.
- Clientes Hibernando: Investir em esforços de marketing para lembrá-los de que já faz um tempo desde a última transação, oferecendo-lhes um incentivo para reavivar os seus investimentos e voltarem a ser clientes recentes.

## Como utilizar este repositório

Para utilizar, basta clonar o repositório e instalar o arquivo requirements.txt em um ambiente Python. Os scripts são bem documentados e podem ser facilmente adaptados para outras análises de dados.

## Possíveis melhorias
Detalhar mais sobre a escolha dos modelos que foram testados e das suas métricas de avaliação. Além disso, seria muito interessante abordar mais sobre os conceitos dos hiperparâmetros utilizados e aplicar métodos de Hiperparameter Tuning para otimizar os resultados das predições.
Me aprofundar mais na divisão dos clusters por perfil de compra, utilizando dados das categorias dos produtos adquiridos.
