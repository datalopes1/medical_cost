# Previsão de Preços - Medical Cost Personal Datasets  
Os dados tem origem no livro "Machine Learning with R" Brett Lantz, a publicação fornece uma introdução ao aprendizado de máquina. Os dados tratam de registros sobre beneficiários de um seguro de saúde nos EUA e vamos utilizá-los para fazer predições e avaliar os fatores que afetam o preço deste produto através da biblioteca Scikit-learn. Os dados podem ser encontrados no [Kaggle](https://www.kaggle.com/datasets/mirichoi0218/insurance) e foram disponibilizados por [Miri Choi](https://www.kaggle.com/mirichoi0218).

![img](https://i.imgur.com/lZnDKsv.jpeg)

## Features
|Coluna|Descrição|
|---|---|
|age|Idade|
|sex|Genêro|
|bmi|O IMC (Índice de Massa Corporal)|
|children|Número de dependentes|
|smoker|Fumante (sim ou não)|
|region|A zona residencial|
|charges|Os custos individuais do seguro|

## Metas e objetivos
O objetivo desse projeto é fazer uma breve análise exploratória e construir um modelo de Machine Learning para predizer preço de seguro saúde.
### Resultados 
#### Insights da Análise Exploratória
- Tabagismo é o fator de maior peso no aumento do valor do seguro de saúde;
- Peso (IMC), e Idade são os outros fatores que tem maior efeito nos preços, hábitos saudáveis além de estender a vida também ajudam na saúde financeira;

### Sobre o modelo 
Com o XGBRegressor alcançamos um modelo com as seguintes métricas:

|Métrica|Resultado
|---|---|
|R2 Score|0.815|
|Mean Squared Error|0.1664
### Ferramentas utilizadas
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)
### Bibliotecas Python utilizadas
#### Manipulação de dados
- Pandas, NumPy.
#### EDA
- Seaborn, Matplotlib.
#### Machine Learning e Feature Engineering
- Scikit-learn, XGBoost.

# Exploratory Data Analysis
### Comportamento do target
![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot1.png?raw=true)

Existe uma forte assimétria na variável dependente, vamos observar com um histograma. 

### Features x target
![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot2.png?raw=true)

Existe uma correlação positiva entre a idade e os preços do seguro. O tabagismo também é um fator que pode pesar nos preços, vamos repetir o gráfico de dispersão mas agora destacando os fumantes.

![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot3.png?raw=true)

Os maiores valores de seguro são pagos por fumantes.

![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot4.png?raw=true)

![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot5.png?raw=true)

É possível observar alguns valores extremos, vamos checar se estes são fumantes.

![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot6.png?raw=true)

Novamente o tabismo se mostra um hábito que encarece o preço do seguro.

![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot7.png?raw=true)

![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot8.png?raw=true)

![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot9.png?raw=true)

### Correlação
![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot10.png?raw=true)

Idade, IMC e o Tabagismo são as principais variáveis relacionadas ao preço do seguro.

# Modelo de Regressão
O modelo utilizado para este projeto foi o XGBRegressor, e tive o seguinte resultado de desempenho com ele:

|Métrica|Resultado
|---|---|
|R2 Score|0.815|
|Mean Squared Error|0.1664|

![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot11.png?raw=true)

![](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot12.png?raw=true)


