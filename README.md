# 🏥 Previsão de Preços de Seguro com Regressão Linear

Projeto baseado no dataset Medical Cost Personal Datasets encontrado no [Kaggle](https://www.kaggle.com/datasets/mirichoi0218/insurance) e disponibilizado por [Miri Choi](https://www.kaggle.com/mirichoi0218).
### 🛠️ Ferramentas utilizadas
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)

## 1.1. A estrutura dos dados

Os dados tem origem no livro "Machine Learning with R" Brett Lantz, a publicação fornece uma introdução ao aprendizado de máquina. Os dados tratam de registros sobre beneficiários de um seguro de saúde nos EUA e vamos utilizá-los para fazer predições e avaliar os fatores que afetam o preço deste produto através da biblioteca Scikit-learn.

#### Os dados seguem a seguinte estrutura:
|Coluna|Descrição|
|-------|---------|
|age|Idade do beneficiário|
|sex|Genêro|
|bmi|O IMC (Índice de Massa Corporal) do beneficiário|
|children|Número de dependentes cobertos pelo seguro|
|smoker|Fumante (sim ou não)|
|region|A zona residencial nos EUA do beneficiário|
|charges|Os custos individuais do seguro|

## 1.2. Importação das bibliotecas e carregamento dos dados
Importei as biblitoecas pandas, numpy, matplotlib, seaborn. E então carreguei o dados através do pd.read_csv()

# 🧱 2. Entendendo os dados
## 2.1. Exploração inicial
Através dos métodos shape, head(), tail() e info() busquei entender a estrutura dos dados. Além disso removi as duplicatas existentes.
# 🔍 3. Análise exploratória de dados
## 3.1. O comportamento das features 
![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot1.png?raw=true)

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot2.png?raw=true)

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot3.png?raw=true)
#### Sobre a visualização
Existe um grande volume dos beneficiários com um IMC que pode ser considerado alto, um índice acima de 25 indica sobrepeso e acima de 30 já se está em obesidade. Sobrepeso e altas percentagens de gordura na composição corporal são questões que afetam muito negativamente a saúde e aumentam índices de diversas doenças, ou seja maior necessidade do uso de serviços de medicina.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot4.png?raw=true)
#### Sobre a visualização
Mais de 40% dos registros do conjunto de dados são de pessoas sem dependentes, o maior volume de pessoas com filhos fica entre 1 e 2. Maior número de dependentes, também indica maior frequência no uso de serviços médicos.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot5.png?raw=true)

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot6.png?raw=true)

## 3.2. O comportamento do target

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot7.png?raw=true)
#### Sobre a visualização
Nosso target mostra um comportamento diferente da normal em sua distribuição. Acredito que será necessário fazer uma transformação logaritimica na variável para adequar ao modelo. Vamos visualizar um boxplot para ter outra perspectiva da distribuição.
![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot8.png?raw=true)
#### Sobre a visualização
Apesar da existência de outliers, pela quantidade limitada de dados vou optar por não remover estes registros.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot9.png?raw=true)

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot10.png?raw=true)
#### Sobre a visualização
Existe uma tendência de aumento de preço, de acordo com aumento da idade. O que é natural, pessoas idosas precisam de maiores cuidados medicos.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot11.png?raw=true)
#### Sobre a visualização
Apesar do equilibrio na distribuição entre homens e mulheres, homens tem custos mais altos de seguro saúde.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot12.png?raw=true)
![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot13.png?raw=true)
#### Sobre a visualização
Existe uma tendência de aumento dos custos de acordo com o IMC, como ressaltado anteriormente sobrepeso é uma comorbidade que torna mais fácil contrair certas condições de saúde.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot14.png?raw=true)
#### Sobre a visualização
Pessoas com dois dependentes tem maiores custos com o seguro, apesar do maior número de beneficiários terem apenas 1 filho ou nenhum.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot15.png?raw=true)
#### Sobre a visualização
Ser fumante é um fator muito preponderante nos custos.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot16.png?raw=true)

# 🤖 4. Regressão Linear
## 4.1. Pré-processamento dos dados
### Transformação logarítmica
Como observado durante a análise exploratória, a distribuição de 'charges' tem uma assimétria. Vou aplicar uma transformação antes de prosseguir.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot17.png?raw=true)
#### Observações
Agora é possível ver uma distribuição mais próxima à normal.

### Definindo os conjuntos X e y
Aqui separei as features do target dentro do conjunto de dados.
### Tratando variáveis com OneHotEncoder
Aqui tratei as variáveis categóricas através do ColumnTransformer e OneHotEncoder.
### Matriz de correlação
![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot18.png?raw=true)

### Definindo conjuntos de treino e teste
Aqui através do train_test_split separei os conjuntos. 

## 4.3. LinearRegression
Aqui través da biblitoeca sklearn treinei um modelo que atingiu as métricas de R2 e Mean Squared Error de 82,95% e 0.15828783951190992 respectivamente.

### Coeficientes de regressão 
![img](https://i.imgur.com/5bbThz1.png)

Estes foram os coeficientes de regressão, e podem ser interpretados de maneira matemática da seguinte forma:
![img](https://i.imgur.com/j9XlHK9.png)

Essa expressão representa o modelo de regressão onde a variável **y** ou 'charges' é modelada como uma função exponencial de 'age', com um intercepto em log. Dessa forma para cada unidade acrescida em 'age' os custos do seguro, assumindo todos os outros fatores constantes, terá um aumento de 3,4%.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot19.png?raw=true)

## 4.4. DecisionTree
Aqui través da biblitoeca sklearn treinei um modelo que atingiu as métricas de R2 e Mean Squared Error de 88,43% e 0.10741950216493398 respectivamente.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot20.png?raw=true)

## 4.5. RandomForest
Aqui través da biblitoeca sklearn treinei um modelo que atingiu as métricas de R2 e Mean Squared Error de 88,36% e 0.10807264743950709 respectivamente.

![img](https://github.com/datalopes1/medical_cost/blob/main/doc/img/plot21.png?raw=true)

## 4.6. Conclusões 
- Com o melhor R2 Score o DecisionTree é o melhor modelo para este caso.
- De acordo com a [OPAS](https://www.paho.org/pt/101-razoes-para-parar-fumar-0) (Organização Pan-Americana de Saúde) fumar é um hábito que diminui em até 10 anos a expectativa média de vida, o cigarro trás ainda maior propensão a várias doenças cronicas, cardiácas e câncer. Fumantes consequentemente vão precisar com maior frequência de serviços de saúde, além disso a idade naturalmente vai tornar um beneficiário do seguro saúde uma pessoa com maior necessidade de atendimentos. Esse dois fatores são os de maior efeito nos custos. 

![img](https://images.unsplash.com/photo-1555441293-6c6fb1eb9773?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)