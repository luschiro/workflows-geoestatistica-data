# Módulo 1 | Qualidade de dados e validação inical

## Introdução

Com nossos dados "raw" permanecidos em uma tabela, vamos começar nossas análises. Uma vez em uma database SQlite, pode utilizar o DB Browser, uma ferramenta simples e bem útil, onde poderemos validar dados, análises e conferir o resultado de nossas queries.

## SQL

O SQL (structured query language) é uma linguagem de consulta antiga (e não de programação..), mas muito útil.

Geralmente, em operações do dia a dia, utilizamos ferramentas de planilha (excel, sheets) para resolvermos problemas. Quando existe um volume muito grande dados, utilizar tais ferramentas pode ser um pouco complicado.

Deste modo, vamos realizar algumas análises utilizando SQL, simulando um contexto fora das ferramentas de planilha. Para praticar, iremos resolver algumas questões..

## DB Browser

O DB Browser é uma ótima ferramenta visual para administração de databases SQlite. Segundo o [site oficial](https://sqlitebrowser.org/):

>DB Browser for SQLite (DB4S) is a high quality, visual, open source tool to create, design, and edit database files compatible with SQLite. DB4S is for users and developers who want to create, search, and edit databases.

Recursos para criação de databases e tabelas SQLite no DB Browser:

* [vídeo 1](https://www.youtube.com/watch?v=4_p0eBgkZuk&ab_channel=CobraDevCursos)
* [playlist](https://www.youtube.com/playlist?list=PLTYLKz3zyxKonrLifrisb02uIjIIVvGnZ)
* [playlist(ENG)](https://www.youtube.com/watch?v=b0syBVINQiI&list=PLU70qqWW4frGdwNh4czgTrCrHvPhyt2aI&ab_channel=MainlyWebStuff)

## Exercícios

Exercício para colocarmos em prática o SQL, tanto para qualidade e validação de dados (A-X), como em contexto de análise.

---

* **Qualidade de Dados - `quality.sql`**
  * **Filtros e Contagens**
    * Quantos pontos foram amostrados?
      * Quais os tipos distintos de uso de terra - landuse e litotipo - Rock?
      * Quantas amostras foram coletadas em floresta?
      * Quantas amostras são do Argoviano e possuem teor de Zn > 50?
        * caso esse seja um teor de corte fictício, classifique as amostras com base neste critério
      * Quantas amostras não possuem dados de teor de Cr?
      * Quantas não possuem teores de Cr ou de Zn?
  * **Agrupamentos**
    * Quantas registros existem de cada `litotipo`?
    * Qual a combinação de `landuse` e `litotipo` que apresenta mais amostras coletadas?
      * crie um rank com as 5 principais combinações
      * filtre as combinações para aquelas com mais de 40 pontos amostrados
    * Existe algum ponto de amostragem repetido, mesma localização?
  * **With**
    * Existe alguma amostra com teor faltante em todos os elementos?
    * Entre cádmio, cobalto e cromio, qual o elemento com o maior número de amostras sem teor?
      * em termos %, o quanto essas amostras representam do total de amostras?
  * **Join**
    * Na tabela `jura_bad_samples` existem amostras que não são confiáveis. Quais os `litotipos` dessas amostras?
    * Quais os maiores teores de Cr e Zn nas amostras problemáticas?
    * Quantas amostras do dataset estão acima desses teores?
      * por exemplo, existem X amostras com teores de Zn acima do teor máximo de Zn nas amostras problemáticas;
    * Monte uma tabela com todos os dados da tabela original e uma coluna adicional de status.

---

* **Sobre os Teores - `teores.sql`**
  * Para cada litotipo, quais os maiores, menores teores de Zn? E o teor médio de Cr?
  * Em qual `landuse` ocorre o maior teor médio de Cu?
  * Quais são as 5 amostras do `Argoviano` com maiores teores de Zn?
  * Qual o teor médio de Cr das amostras que possuem teor acima do limite Q3?
  * Considerando a [definição de outliers por IQR](https://towardsdatascience.com/why-1-5-in-iqr-method-of-outlier-detection-5d07fdc82097), quais amostras apresentam outliers?
    * qual elemento possui o maior número de amostras anômalas segundo esse critério?

---

* **Novas Tabelas**
  * **Tabela I -  `new_table_I.sql`** Monte uma visão nova a nível de amostra:
    * sem dados faltantes;
    * nomes de colunas padronizados;
    * status de amostra problemática;
    * com flags para outliers de Zn, segundo o critério de IQR;
  
  * **Tabela II -  `new_table_II.sql`** Monte uma visão ou tabela mais abstrata, a nível de litotipo & landuse.
    * Quais tipos de informações poderíamos agregar?
