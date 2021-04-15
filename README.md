# lap1
# DISCIPLINA: Laboratório de Pesquisa 1 - lap1

# TRABALHO 01:  Machine Learning

# Sumário

## 1. Componentes <br>
Integrantes do grupo<br>
Helen França Medeiros: helenfranca93@gmail.com<br>
Mayke Willans Christo Pereira: maykewillans@hotmail.com<br>
Lia Casati: liac.ramaldes@gmail.com
<br>

## 2. Apresentação dos Datasets (Clássico + Em estudo)
    Visão geral das bases de dados:
        a) seus dados são sobre o que?
        b) o que você deseja com este conjunto de dados?
        c) quais são os tipos de atributos existentes e qual é o atributo alvo?
        d) quais são os problemas existentes?
        e) qualidade e clareza: garantir que a semântica dos atributos seja clara (nomes coerentes com os dados, se necessário renomear atributos).

>#### 2.1 Visão geral da base de dados clássica:<br>

### **Dataset Titanic**
**Seus dados são sobre o que?**
<br>
O naufrágio do Titanic é um dos mais famosos da história. Em 15 de abril de 1912, durante sua viagem inaugural, o Titanic afundou após colidir com um iceberg. 
Infelizmente, não havia botes salva-vidas suficientes para todos a bordo, resultando na morte de 1.502 dos 2.224 passageiros e tripulantes. Embora houvesse algum elemento de sorte envolvido na sobrevivência, parece que alguns grupos de pessoas tinham mais probabilidade de sobreviver do que outros.

O dataset Titanic possui informações sobre os passageiros presentes na embarcação.

**O que você deseja com este conjunto de dados?**
<br>O objetivo é deste trabalho é prever se, dado determinadas características uma pessoa, a mesma sobreviveria ou não.

**Quais são os tipos de atributos existentes e qual é o atributo alvo?**
<br>Atributo alvo é a coluna Survived

| Atributo | Tipo | Significado |
| :------------ |:--------------|:---------|
| PassengerId  | Numérico discreto | Número de identificação do passageiro |
| Survived     | Categórico binário | Informa se o passageiro sobreviveu ao desastre |
| Pclass       | Categórico ordinal? | Classe do bilhete (1, 2 3) |
| Name       | Categórico nominal | Nome do passageiro |
| Sex       | Categórico nominal| Sexo do passageiro |
| Age       | Numérico contínuo| Idade do passageiro |
| SibSp       | Numérico discreto| Quantidade de cônjuges e irmãos a bordo |
| Parch       | Numérico discreto| Quantidade de pais e filhos a bordo |
| Ticket       | Categórico nominal| Número da passagem |
| Fare       | Numérico contínuo| Preço da Passagem |
| Cabin       | Categorico nominal| Número da cabine do passageiro |
| Embarked       | Categórico nominal| Porto no qual o passageiro embarcou (C = Cherbourg, Q = Queenstown, S = Southampton) |
<br>

**Quais são os problemas existentes?**
<br>Valores ausentes e violação de domínio
<br><br>

>#### 2.2 Visão geral da base de dados em estudo:<br>
<br>

### **Dataset Mania**
**Seus dados são sobre o que?**
<br>A mania é caracterizada por humor eufórico, redução do sono, aumento da energia e interesse em diversos objetivos/projetos ao mesmo tempo, assim como aumento da libido e inquietação. Durante os episódios de mania, o pensamento torna-se muito rápido, podendo prejudicar a formação de ideias e a comunicação, o que faz com que a pessoa transmita ideias delirantes, que muitas vezes fogem da realidade.

O dataset Mania possui informações informações relevantes para a detecção do transtorno comum mania.

**O que você deseja com este conjunto de dados?**
<br>O objetivo deste trabalho é fazer uma análise para verificar se uma pessoa pode ter ou não episódios de mania.

**Quais são os tipos de atributos existentes e qual é o atributo alvo?**
<br>Em geral, os tipos de atributos são:
- Dados nominais:
    - Exemplo: Tem problemas nas costas ou no pescoço? Resp.: 1(sim), 5(não), 8(não sabe) e 9(recusou)
- Dados discretos:
    - Exemplo: Qual a sua idade? Resp.: 18
- Dados binários:
    - Exemplo: Tem medo de insetos/animais? Resp.: 1(sim) ou 5(não)

Atributo alvo: **dsm_man**

**Quais são os problemas existentes?**
- Grande quantidade de valores ausentes;
- Registros sem significados ou informação relevante;
    - Exemplo: CC50C - Você está atualmente coberto por algum dos seguintes...
- Inconsistencia: existem colunas que se complementam, mas são interpretadas de forma diferente;
    - Exemplo: M6B1 (duração do episódio sendo muito irritável que se destaca) e M6B2 (Unidade de tempo), assim poderíamos ter: 2 dias, 2 meses, 2 anos, etc.
- Atributo alvo possui muitos valores de uma classe e poucos de outra;
<br><br>

### 3.Pré-processamento dos Datasets <br>

Realize o Pré-processamento e Tratamento de Dados em sua base/dataset.

>#### 3.1 Pré-processamento e tratamento na base de dados clássica:<br>

A imagem abaixo é um exemplo do conteúdo da base de dados Titanic e sua estatística
![head](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/head.PNG)

![describe1](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/describe1.PNG)

Muitas colunas(Age, Cabin, Embarked) apresentavam dados nulos e tratamos das maneiras a seguir. A coluna Fare notamos uma incoerência analisando o describe, e decidimos investigar também.

![nulos](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/nulos.PNG)



___
**Age**

Visando maior acerto na imputação dos dados, nos apoiamos na média de idade contando com duas variáveis: Sex e Title (coluna criada com o pronome de tratamento extraído do nome do passageiro. Para tal utilizados a função extrairTitulo())

Decidimos usar a coluna Sex a partir do resultado da média de idades diferentes para o tratamento de DR. No caso do sexo Feminino a média é de 49 anos e no sexo Masculino a média é de 40 anos.

![extrairTitulo](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/extrairTitulo.PNG)
![média_idade_title](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/média_idade_title.PNG)

Imputando os valores

![input_idade_media_titulo](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/input_idade_media_titulo.PNG)

___

**Cabin**

Com cerca de 77% de nulos

![cabin_null](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/cabin_null.PNG)

Os dados da coluna Cabin são conjuntos de letras e números. Abaixo utilizamos a primeira letra do campo para classificar em cada Classe.

![cabin_letra](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/cabin_letra.PNG)

Separando as cabines por classe, temos:

* Classe 1 - A, B, C, D, E, T
* Classe 2 - D, E, F
* Classe 3 - E, G, F

Vamos de forma randômica imputar esses dados por cada classe.

![input_cabin](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/input_cabin.PNG)

Por fim, vamos aplicar a técnica One-Hot Encoding na coluna Cabin. Como são dados categóricos e em pouca quantidade fica livre da 'maldição de dimensionalidade'

![onehot_cabin](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/onehot_cabin.PNG)

Resultado:

![cabin_hot](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/cabin_hot.PNG)

Como só temos 1 registro na cabine T, vamos desconsiderá-la do dataset

![exclusao_T](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/exclusao_T.PNG)


___

**Sex**

Substituindo

* Female por 1
* Male por 0

![sex](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/sex.PNG)


___

**Embarked**

Aqui também vamos aplicar a técnica One-Hot Encoding pelo mesmo motivo anterior.

![onehot_embarked](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/onehot_embarked.PNG)

___

**Fare**

Observando a coluna Fare pelo describe vimos que a média e mediana estão muito distantes. Possivelmente outliers, por isso decidimos investigar.

![box1](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/box1.PNG)

![box2](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/box2.PNG)

Como pode-se observar, existem muitos outliers. Nas próximas linhas vamos tratar essa questão.

* Contagem de pessoas que pagaram mais de 90 'dinheiros' de passagem

* Contagem de pessoas por classe

![classe_alto_valor](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/classe_alto_valor.PNG)

* Observações:
Tendo por base o gráfico tomamos o valor 90 como sendo o início dos outliers. Dessa maneira verificamos a quantidade de passageiros que haviam pago esse valor acima do normal e a qual classe pertenciam. Chegamos a conclusão que os passageiros que pagaram valores absurdos eram os da primeira classe, o que faz sentido já que essa é a classe mais cara na teoria - quanto melhor a classe, mais cara ela é. Porém esses pagaram valores muito diferentes dos outros.
De 216 passageiros na primeira classe, 57 pagaram um valor acima da média esperada.

* Abordagem utilizada:
Iremos utilizar a média de preço da primeira classe (retirando outliers) para consertar esses valores e não interferir nos resultados, trazendo a normalidade.

![preco_medio](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/preco_medio.PNG)

![func_fare_outliers](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/func_fare_outliers.PNG)

![fare_ok](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/fare_ok.PNG)

![box3](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/box3.PNG)


Desconfiamos que houvesse ainda uma distância entre os valores por conta dos passageiros que constam como passagem com valor zero, porém ao ver a quantidade percebemos que era bem baixa (15) se comparado com o número total de passageiros.

___

**Alguns ajustes:**

Apagando colunas com dados categóricos que não nos seriam úteis mais

![drop_categorico](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/drop_categorico.PNG)

___

**Versão final**

![final](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/final.PNG)

______

>#### 3.2 Pré-processamento e tratamento na base de dados em estudo:<br>
**Verificando valores nulos:**

![dataset_mania_nulos](./imagens/dataset_mania_nulos.png)

Podemos observar a presença de muitos valores nulos (representados em amarelo).

**Visualizando atributo alvo:**

![dataset_mania_target](./imagens/dataset_mania_target.png)

Podemos notar que o dataset possui muitos exemplos da classe 1 (sim) e poucos exemplos da classe 2 (não), precisaremos utilizar técnicas de balanceamento ou enriquecimento de dados para tratar a situação.

**Tratando valores nulos:**

Como encontramos muitos valores nulos, nossa ideia inicial foi tentar reduzir esses registros por meio da exclusão. Assim, excluímos colunas que apresentavam mais de 75% de valores nulos, como pode-se observar na imagem a seguir:

![dataset_mania_tratamento_nulos](./imagens/dataset_mania_tratamento_nulos.png)

No entanto, percebemos que todas as colunas de M foram retiradas, então talvez não seja a melhor abordagem a se fazer.

A segunda opção foi analisar individualmente M, SC e CC.

Visualizando nulos em M:

![dataset_mania_M_nulos](./imagens/dataset_mania_M_nulos.png)

Visualizando nulos em SC:

![dataset_mania_SC_nulos](./imagens/dataset_mania_SC_nulos.png)

Visualizando nulos em CC:

![dataset_mania_CC_nulos](./imagens/dataset_mania_CC_nulos.png)

Neste dataset, as perguntas feitas pelo entrevistador podem mudar conforme as respostas dos entrevistados. Este fato se dá pois, ao obter determinada informação, o entrevistador realiza o diagnostico do entrevistado e procura fazer perguntas mais específicas para ter a possibilidade de detectar, por exemplo, um transtorno comum.
Com base nessas informações, vamos atribuir o valor 0 nos registros em M que não possuem valores.

Como ainda não possuímos muitas informações sobre a importância dos registros em SC e CC, vamos excluir colunas que possuem pelo menos 1 valor nulo.

Visualizando M:

![dataset_mania_M](./imagens/dataset_mania_M.png)

Visualizando SC:

![dataset_mania_SC](./imagens/dataset_mania_SC.png)

Visualizando CC:

![dataset_mania_CC](./imagens/dataset_mania_CC.png)
 
**Excluindo Informações sem significado**<br>
Analisando cada atributo, podemos perceber que existem atributos de informações do entrevistador. Para a nossa análise, esses dados não possuem significado relevante. E por isso serão excluidos : CC11,CC21,CC23,CC25,CC27,CC29,CC7,CC8,M1A,M21A,M26,M28,M29_1,M54,M55,M8,SC1_1 e SC28.

**Excluindo atributos sem registros**<br>
Pelo domínio das respostas que geramos anteriormente, podemos perceber que há colunas retornaram resultados. Logo, são colunas vazias e que podem ser excluídas. São elas CC2A04,CC2A05,CC2A06,CC2A07,CC2A08,CC2A09,CC2A10,CC2A11 e CC2A12.

**Tratando atributos de tempo**<br>
No dataset, existem colunas que se complementam, mas são interpretadas de forma diferente.

Exemplo:
M6B1 - Duração do episódio sendo muito irritável que se destaca
M6B2 - Unidade de tempo
Assim, poderíamos ter: 2 dias, 2 meses, 2 anos, etc.

Vamos tratar esses valores transformando todos os registro para uma única unidade de tempo. Escolhemos a unidade de tempo "hora" para a padronização.


### 4.Análise Exploratória dos datasets<br>

>#### 4.1 Análise exploratória na base de dados clássica:<br>

A partir dos gráficos a seguir podemos inferir que:

* O número de mortos passou o de sobreviventes
* Morreram mais homens que mulheres
* A classe em que mais morreram pessoas foi a 3ª (Mediante a essas informações, porém se fizéssemos um balanceamento pode ser que a quantidade significativa mude).

![plot1](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/plot1.PNG)
![plot2](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/plot2.PNG)
![plot3](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/plot3.PNG)
![plot4](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/plot4.PNG)

Fizemos o uso do **Pandas Profiling**

![pandas1](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/pandas1.PNG)

O Pandas Profiling acusou cerca de 11.9% dos dados como duplicados. Retiramos e a nova e última versão do dataset é de 785 registros.

![warning](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/warning.PNG)

Além disso também acusou correlações entre algumas variáveis, porém não investigamos a fundo.

___

**PLUS**

![predicao](https://github.com/helenfranca/lap1/blob/8b34ff5205ff229f7d2f4caec57709f0c4a37d0a/img_titanic/predicao.PNG)

Aplicamos o teste de predição e taxa foi de 79.42% de acurácia nos dados de treinamento e usando a parte não treinada foi de 72.58%.

Porém ao realizarmos o mesmo procedimento com a base sem retirar os duplicados, o resultado teve uma leve melhora na acurácia principalmente utilizando a faixa não treinada.

Resultados:

* Sem duplicados:

  * Treino: 79.42%
  * Sem Treino: 72.58%

* Com duplicados:

  * Treino: 79.64%
  * Sem treino: 79.82%



>#### 4.2 Análise exploratória na base de dados em estudo:<br>
![dataset_mania_analise_target](./imagens/dataset_mania_analise_target.png)

Como constatamos, o atributo alvo poderia ser tratado aplicando técnicas de balanceamento ou enriquecimento de dados.

Outro ponto a destacar é que podemos observar algumas correlações que podem ser utilizadas como técnicas de seleção de caracteríticas para escolher melhores atributos.

Visualizando correlações em M:

![dataset_mania_M_correlations](./imagens/dataset_mania_M_correlations.png)

Visualizando correlações em SC:

![dataset_mania_SC_correlations](./imagens/dataset_mania_SC_correlations.png)

Visualizando correlações em CC:

![dataset_mania_CC_correlations](./imagens/dataset_mania_CC_correlations.png)

Por fim, analisando os dados coletados até aqui, uma possível análise para realizar posteriormente seria tratar cada atrituto individualmente, reduzindo a dimensionalidade e possibilitando uma melhor compreensão do dataset.

>Sugestão: Utilizar ferramentas como Pandas Proffile e Sweetviz , Seaborn e Matplotlib <br>
    
[Tutorial básico com Seaborn](https://github.com/profmoisesomena/escience_and_tools/blob/master/seaborn/Seaborn_introduction.ipynb "Seaborn Introduction")

># Marco de Entrega 01: Itens do Sprint 01 <br>
    
### 5.Estudo dos algoritmos previamente definidos para a pesquisa
  Os algoritmos definidos para a pesquisa foram: Gradient Boost Classifier, Extreme Gradient Boosting e CatBoost Classifier.

Para compreendermos melhor o funcionamento cada um dos algoritmos, vamos conhecer alguns conceitos:

**Ensemble Learning (aprendizagem em conjunto)** são métodos que visam formar um novo modelo combinado outros existentes. Esse agrupamento busca associar os algoritmos de forma a minimizar suas desvantagens individuais no modelo final.

Os métodos **Boosting** formam uma categoria de Ensemble Learning, tendo como base treinar vários modelos mais simples com a finalidade de produzir um modelo final mais robusto. Para maximizar o desempenho do preditor final, o Boosting treina iterativamente novos modelos com um enfoque nas observações que os modelos anteriores erraram mais, tornando a predição mais resistente ao viés. Em seguida, atualiza-se o modelo para priorizar as predições com maior erro nas observações da base de teste. O modo como ocorre esse treinamento e essa atualização é onde diferem os diferentes algoritmos de Boosting.
<br>
#### 5.1 Visão geral sobre cada um dos algoritmos:<br>
   
### **Gradient Boost**

**A) Explicação sobre o algoritmo/método de classificação adotado (como funciona, performance/complexidade para treino e para execução, etc...)**

Gradiente Boost é um algoritimo que tem como finalidade prever valores continuos. Ele é baseado em árvores de decisão e trabalha de forma a melhorar as previsões futuras com base nos erros das anteriores. Funciona calculando residuos, sendo estes o dado previsto menos o dado original, conforme a diferença entre os residuos diminui ele chega mais próximo ao resultado, as previsões são feitas seguindo a seguinte formula "previsão2 = previsão1 + (nota x residual)", sendo a nota um valor entre 0 e 1 responsável por minimizar o overfit. Tem uma complexidade grande devido seus calculos e uma performace que deve ser analisada com cuidado pois esse algoritmo pode gerar overfit.
    
**B) Estudar e apresentar exemplo de aplicações com algoritmos:**
É um algoritimo que pode ser usado tanto para classificação como para regressão.
   
**C) Existem requisitos/premissas necessárias para aplicação do algoritmo, quais são?**

Não aceita valores categoricos e precisa de um algoritmo que tenha erros, uma vez que sua predição é baseada nos erros.
    
**D) Aplicar os modelos estudados em bases de dados clássicas como Iris/Titanic**

<br>

### **CatboostClassifier**

É uma técnica de Machine Learning focado em melhoria na velocidade computacional baseado no Gradient Boost. Utilizado para classificação, seu funcionamento se assemelha a técnica em que se baseia, porém o que a diferencia é a maneira em que trata os dados categóricos onde implementa árvores simétricas utilizando One-hot-encoding. Para bases muito grandes, esta técnica permite o uso da GPU. O CatboostClassifier é de fácil configuração para treino e tende a oferecer ótimos resultados mesmo com hiperparâmetros padrões.

Esse procedimento é muito propenso ao overfitting, porque é realizando utilizando resíduos de cada ponto de um modelo que já foi treinado no mesmo conjunto de pontos. O CatboostClassifier treina o modelo usando os resíduos(erros) de cada ponto de dados como valores de classe, realizando o monitoramento de erros/perda. Neste cálculo usa o modelo que foi treinado em todos os outros pontos anteriores a ele. Por exemplo, para calcular o resíduo do ponto x5, treina um modelo usando os pontos x1, x2, x3 e x4. Portanto treina diferentes modelos para pontos diferentes. No final, é calculado os resíduos para os pontos onde o modelo correspondente nunca foi treinado.

Segundo a documentação ele tende a ser até 8x mais rápido que outros algoritmos de mesma finalidade, como o XGboost durante a previsão. Porém se os dados, em sua maioria, forem numéricos tende a ser mais demorado que o LightGBM, outro algoritmo de Machine Learning.

<br>

**B) Estudar e apresentar exemplo de aplicações com algoritmos:**

Este algoritmo costuma ser aplicado em desafios de negócio, como detecção de fraude; Recomendação; Previsões;

<br>

**C) Existem requisitos/premissas necessárias para aplicação do algoritmo, quais são?**

Este algoritmo não exige muito esforço no pré-processamento dos dados se comparados com outros tipos de algoritmos, já que aceita dados categóricos.

Para que não hajam erros na criação do modelo, é interessante informar as colunas queu são categóricas. 

**D) Aplicar os modelos estudados em bases de dados clássicas como Iris/Titanic**

### **Extreme Gradient Boosting**
**A) Sobre o algoritmo/método de classificação adotado**
<br>Extreme Gradient Boosting ou XGBoost, é um algoritmo de aprendizado de máquina, baseado na estrutura do Gradient Boosting. Como podemos perceber pelo nome, o XGBoost é um Gradient Boosting melhorado, combina técnicas de otimização de software e hardware para produzir resultados superiores usando menos recursos de computação no menor período de tempo.

Funcionamento:
1. O algoritmo faz uma predição inicial;
2. Assim como o Gradient Boosting, o XGBoost treina uma árvore de decisão verificando os resíduos.
    <br>2.1 Cada árvore começa com uma única folha, e todos os resíduos vão para essa folha;
    <br>2.2 Calculamos um score de qualidade, ou score de similaridade, para os resíduos;
    <br>2.3 Tentamos agrupar resíduos similares dividindo em dois grupos criando duas folhas;
    <br>2.4 Agora calculamos os scores de similaridade para as duas folhas;
    <br>2.5 Precisamos então quantificar o quão melhor é termos essa divisão de folhas comparadas a quando todas estavam na raíz. Fazemos isso calculando o ganho.
3. Esse procedimento é refeito e agrupamos as divisões com melhores ganhos;
4. Calculamos o output para cada folha
5. Temos uma árvore completa. Assim, o XGBoost faz novas predições com a predição inicial mais o output da árvore vezes uma learning rate (taxa de aprendizado).

**B) Estudar e apresentar exemplo de aplicações com algoritmos**
<br>

**C) Existem requisitos/premissas necessárias para aplicação do algoritmo, quais são?**
<br> O algoritmo não trabalha com dados categóricos

**D) Aplicar os modelos estudados em bases de dados clássicas como Iris/Titanic**
<br>


![matrizdeconfusao](https://github.com/helenfranca/lap1/blob/helen/img_results/matriz_de_confusao.PNG?raw=true)

    
#### 5.2 Qual dos algoritmos estudados (não visão do grupo, com base nos resultados obtidos) é o mais recomendado para a base de dados clássica utilizada (explicar):<br>
Com base nos resultados, o algoritmo com melhor desempenho foi o XGBoost.

![besttitanic](https://github.com/helenfranca/lap1/blob/helen/img_results/best_titanic.PNG?raw=true)


<br>

#### 5.3 Qual dos algoritmos estudados (não visão do grupo) provavelmente será o mais recomendado para a base de dados em estudo (explicar):<br>

O Catboost tem melhor desempenho com dados categóricos, como o dataset Mania possui apenas valores numéricos, não seria recomendado utilizá-lo.
Observando as opções restantes, o XGBoost teve um desempenho melhor que o Gradiente Boosting nos testes realizados. Assim, o XGBoost é o mais recomendado para utilização no dataset Mania.


![bestmania](https://github.com/helenfranca/lap1/blob/helen/img_results/best_mania.PNG?raw=true)


># Marco de Entrega 02: Itens do Sprint 02 <br>
>

### 6.Implementar método no dataset em estudo  (explicação + datasets)<br>
    A) Explicação sobre o processo de aplicação dos algoritmos em estudo 
    no conjunto de dados em estudo (passos necessários/realizados)
    B) Implementar método nos datasets utilizados comparar resultados obtidos 
    e validar ou descartar hipótese do ítem 5.1 e 5.2.

![comparacao](https://github.com/helenfranca/lap1/blob/helen/img_results/comparacao_algoritmos.PNG?raw=true)

<br>

![acuraria](https://github.com/helenfranca/lap1/blob/helen/img_results/acuracia.PNG?raw=true)
    
>#### 6.1 Detalhamento dos processos de classificação com base nos algoritmos na base de dados em estudo:<br>
>...
>

### 7.Análise dos resultados obtidos <br>
    A) Detalhar conclusões com base nos resultados obtidos
    B) Definir quais trabalhos futuros podem ser realizados a partir das conclusões obtidas e tarefas realizadas.
    
#### 7.1 Conclusões com base nos resultados obtidos:<br>
Podemos perceber que cada etapa do Machine Learning, desde a preparação dos dados até a avaliação dos resultados da predição, é um processo de aprendizado onde deve-se ponderar cada decisão tomada, observar os impactos e procurar melhorar com base nos resultados obtidos.

Como o dataset Titanic é uma base clássica e com um domínio conhecido, foi mais simples interpretar os atributos, permitindo a realização de testes e análises mais objetivas.

Já no dataset Mania, os dados possuíam pouco ou nenhum significado, tornando o processo mais trabalhoso. Assim, o pré-processamento dos dados, além de preparar os dados, também serviu para o entendimento da base. 
Outro ponto muito importante e que teve um grande impacto nos testes do Mania, foi o grande desbalanceamento do atributo alvo. Esse desbalanceamento é análogo ao processo de Machine Learning em fraudes bancárias, onde temos grande discrepância nos casos, sendo os casos de fraude uma porcentagem mínima. Com isso, para obtermos um resultado mais assertivo, seria mais adequado mudar a ênfase do nosso questionamento inicial: o resultado da análise no dataset Mania não deve prever se pessoa pode ter epsódios de mania ou não, deve prever se, dentre as características apresentadas, uma pessoa apresenta um comportamento diferente do comum e pode ser classificada como um caso suspeito, devendo ser observada com mais cuidado.

>#### 7.2 Trabalhos futuros:<br>
>...
>
### 8. Resultados e Artefatos
>#### 8.1 Slides Finais

[Sprint 2](https://docs.google.com/presentation/d/1DifUAMpFXQ_FjF15LCpWkrTEek7UTZRF24Elvk4qNgY/edit#slide=id.p)
[Sprint 3](https://docs.google.com/presentation/d/1MEKfM3S0nKfEmoJaIr2Ga4yqnNoZk5dh-johtPsP8eU/edit)

>#### 8.3 Demais artefatos solicitados pelo professor


># Marco de Entrega 03: Conclusão das atividades <br>

### 9 FORMATACAO NO GIT:<br> 
https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

    
### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. <strong>Caso existam arquivos com conteúdos sigilosos<strong>, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário do git "profmoisesomena", para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.

Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")




