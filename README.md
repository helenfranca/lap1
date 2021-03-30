# lap1
# DISCIPLINA: Laboratório de Pesquisa 1 - lap1

# TRABALHO 01:  Título do Trabalho
Trabalho desenvolvido durante a disciplina:

# Sumário

### 1. Componentes <br>
Integrantes do grupo<br>
Helen França Medeiros: helenfranca93@gmail.com<br>
Mayke Willans Christo Pereira: maykewillans@hotmail.com<br>
Lia Casati: liac.ramaldes@gmail.com
...<br>

### 2.Apresentação dos Datasets (Clássico + Em estudo)<br>
<br>Visão geral das bases de dados<br>

>#### 2.1 Visão geral da base de dados clássica:<br>

##### Titanic 
* Seus dados são sobre o que?
<br>**Resp**: O dataset Titanic possui informações sobre os passageiros presentes na embarcação.
* O que você deseja com este conjunto de dados?
<br>**Resp**: O objetivo é fazer uma análise sobre quais variáveis tiveram maior influência na probabilidade de sobrevivência, ou seja, que tipo de pessoa teve mais chance de escapar com vida.
* Quais são os tipos de atributos existentes e qual é o atributo alvo?
<br>**Resp**: Atributo alvo é a coluna **Survived**

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

* Quais são os problemas existentes?
<br>**Resp**: Incompletude(atributo ausente); Inconsistência(Fare)
* Qualidade e clareza:
<br>**Resp**: Não foi necessário renomear campos e colunas pois estava compreensível.

>#### 2.2 Visão geral da base de dados em estudo:<br>

### **Dataset Mania**
**Seus dados são sobre o que?**
<br>O dataset Mania possui informações informações relevantes para a detecção do transtorno comum mania.

**O que você deseja com este conjunto de dados?**
<br>O objetivo deste trabalho é fazer uma análise sobre quais variáveis têm maior influência na probabilidade de uma pessoa ter episódios de mania.

**Quais são os tipos de atributos existentes e qual é o atributo alvo?**
<br>Em geral, os tipos de atributos são:
- Dados nominais:
    >Exemplo: Tem problemas nas costas ou no pescoço? Resp.: 1(sim), 5(não), 8(não sabe) e 9(recusou)
- Dados discretos:
    >Exemplo: Qual a sua idade? Resp.: 18
- Dados binários:
    >Exemplo: Tem medo de insetos/animais? Resp.: 1(sim) ou 5(não)

Atributo alvo: **dsm_man**

**Quais são os problemas existentes?**
- Grande quantidade de valores ausentes;
- Registros sem significados ou informação relevante;
    >Exemplo: CC50C - Você está atualmente coberto por algum dos seguintes...
- Inconsistencia: existem colunas que se complementam, mas são interpretadas de forma diferente;
    >Exemplo: M6B1 (duração do episódio sendo muito irritável que se destaca) e M6B2 (Unidade de tempo), assim poderíamos ter: 2 dias, 2 meses, 2 anos, etc.
- Atributo alvo possui muitos valores de uma classe e poucos de outra;

**Qualidade e clareza: garantir que a semântica dos atributos seja clara (nomes coerentes com os dados, se necessário renomear atributos).**
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
  (explicação/teoria)<br>
  >#### 5.1 Visão geral sobre cada um dos algoritmos:<br>
    A) Explicação sobre o algoritmo/método de classificação adotado
    (como funciona, performance/complexidade para treino e para execução, etc...)
    B) Estudar e apresentar exemplo de aplicações com algoritmos
    C) Existem requisitos/premissas necessárias para aplicação do algoritmo, quais são?
    D) Aplicar os modelos estudados em bases de dados clássicas como Iris/Titanic 
    (no caso de desejar utilizar outra base consultar o professor)
    
>#### 5.2 Qual dos algoritmos estudados (não visão do grupo, com base nos resultados obtidos) é o mais recomendado para a base de dados clássica utilizada (explicar):<br>
>...
>#### 5.3 Qual dos algoritmos estudados (não visão do grupo) provavelmente será o mais recomendado para a base de dados em estudo (explicar):<br>
>...


># Marco de Entrega 02: Itens do Sprint 02 <br>
>

### 6.Implementar método no dataset em estudo  (explicação + datasets)<br>
    A) Explicação sobre o processo de aplicação dos algotítmos em estudo 
    no conjunto de dados em estudo (passos necessários/realizados)
    B) Implementar método nos datasets utilizados comparar resultados obtidos 
    e validar ou descartar hipótese do ítem 5.1 e 5.2.
    
>#### 6.1 Detalhamento dos processos de classificação com base nos algoritmos na base de dados em estudo:<br>
>...
>

### 7.Análise dos resultados obtidos <br>
    A) Detalhar conclusões com base nos resultados obtidos
    B) Definir quais trabalhos futuros podem ser realizados a partir das conclusões obtidas e tarefas realizadas.
    
>#### 7.1 Conclusões com base nos resultados obtidos:<br>
>...
>#### 7.2 Trabalhos futuros:<br>
>...
>
### 8. Resultados e Artefatos
>#### 8.1 Slides Finais
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




