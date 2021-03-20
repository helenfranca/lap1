# lap1
# DISCIPLINA: Laboratório de Pesquisa 1 - lap1

# TRABALHO 01:  Título do Trabalho
Trabalho desenvolvido durante a disciplina:

# Sumário

### 1. Componentes <br>
Integrantes do grupo<br>
Helen França Medeiros: helenfranca93@gmail.com<br>
Mayke Willans Christo Pereira: maykewillans@hotmail.com<br>
Lia Casati: liac.ramaldes@gmail.com<br>

### 2.Apresentação dos Datasets (Clássico + Em estudo)<br>
<br>

>#### 2.1 Visão geral da base de dados clássica:<br>
<br>

### **Dataset Titanic**
**Seus dados são sobre o que?**
<br>O dataset Titanic possui informações sobre os passageiros presentes na embarcação.

**O que você deseja com este conjunto de dados?**
<br>O objetivo é fazer uma análise sobre quais variáveis tiveram maior influência na probabilidade de sobrevivência, ou seja, que tipo de pessoa teve mais chance de escapar com vida.

**Quais são os tipos de atributos existentes e qual é o atributo alvo?**
<br>Atributo alvo é a coluna Survived

| Atributo | Tipo | Significado |
| :------------ |:--------------|:---------|
| PassengerId  | Numérico discreto | Número de identificação do passageiro |
| Survived     | Categórico binário | Informa se o passageiro sobreviveu ao desastre |
| Pclass       | Categórico nominal | Classe do bilhete (1, 2 3) |
| Name       | Categórico nominal | Nome do passageiro |
| Sex       | Categórico nominal| Sexo do passageiro |
| Age       | Numérico contínuo| Idade do passageiro |
| SibSp       | Numérico discreto| Quantidade de cônjuges e irmãos a bordo |
| Parch       | Numérico discreto| Quantidade de pais e filhos a bordo |
| Ticket       | Categórico nominal| Número da passagem |
| Fare       | Numérico contínuo| Preço da Passagem |
| Cabin       | Categorico nominal| Número da cabine do passageiro |
| Embarked       | Categórico nominal| Porto no qual o passageiro embarcou (C = Cherbourg, Q = Queenstown, S = Southampton) |

**Quais são os problemas existentes?**
<br>Valores ausentes

**Qualidade e clareza: garantir que a semântica dos atributos seja clara (nomes coerentes com os dados, se necessário renomear atributos).**
<br><br>
>#### 2.2 Visão geral da base de dados em estudo:<br>
<br>

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
>Explore conjunto de dados por meio de uma ferramenta (EDA), destacando em suas observações o que for considerado mais relevante.

>#### 4.1 Análise exploratória na base de dados clássica:<br>



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




