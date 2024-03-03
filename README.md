# My-SQL-completo

Nesse repositório, irei demostrar minhas habilidades em 3 bancos de dados: : MySQL, SQL Server e Oracle e também será introduzido às linguagens T-SQL e PLSQL. Também verei a Linguagem SQL do básico ao avançado.

# introdução ao My SQL

O MySQL é um sistema de gerenciamento de banco de dados relacional (RDBMS) de código aberto, amplamente utilizado para armazenar, organizar e gerenciar dados. Desenvolvido pela Oracle Corporation, o MySQL é uma escolha popular entre desenvolvedores devido à sua confiabilidade, desempenho e facilidade de uso.

Banco de Dados Relacional:

O MySQL segue o modelo de banco de dados relacional, que organiza dados em tabelas inter-relacionadas.
Cada tabela contém linhas e colunas, onde as colunas representam os diferentes atributos dos dados e as linhas representam as entradas individuais.
Linguagem SQL:

A interação com o MySQL é feita principalmente através da Linguagem de Consulta Estruturada (SQL), que é uma linguagem padrão para gerenciar bancos de dados relacionais.
Com SQL, você pode realizar operações como seleção, inserção, atualização e exclusão de dados.
Comandos Básicos:

Alguns comandos básicos incluem:
SELECT: Recupera dados de uma ou mais tabelas.
INSERT: Adiciona novos registros a uma tabela.
UPDATE: Modifica os dados existentes em uma tabela.
DELETE: Remove registros de uma tabela.
Chaves Primárias e Estrangeiras:

O MySQL permite a definição de chaves primárias para identificar exclusivamente cada registro em uma tabela.
Chaves estrangeiras são usadas para estabelecer relações entre tabelas, garantindo a integridade referencial.
Índices:

Os índices são utilizados para otimizar a velocidade de recuperação de dados, tornando as consultas mais eficientes.
Índices são criados em colunas específicas para acelerar a busca.
Administração e Segurança:

O MySQL oferece ferramentas e comandos para administrar o banco de dados, como criar usuários, conceder permissões e realizar backups.
Suporte à Transações:

Suporta transações para garantir a consistência dos dados. Você pode usar o comando COMMIT para confirmar as alterações ou ROLLBACK para desfazê-las.

# Modelagem na prática simples

O cliente Tera Comércio de Produtos S.A, solicitou a modelagem de um banco de dados para cadastro dos seus clientes.
A função da Unidados é a análise dos requisitos junto aos usuários para a correta construção do produto. O cliente deseja que inicialmente os scripts sejam construídos para o Banco de Dados MySQL, porém, posteriormente pode haver mudança no ambiente e consequentemente adaptação dos scripts para outros produtos de SGBD.
O cliente não quer nenhuma informação relativa à vendas ou estoque, desejando somente as informações primárias de Clientes.

O nosso cliente solicitou uma tabela para armazenar os livros que são comercializados pela empresa. A solicitação é somente para livros e não há a necessidade de realizar busca em outras tabelas. Hoje há um funcionário de vendas que tem uma tabela do Excel para guardar esses registros, mas as buscas estão ficando complexas. Decidiu-se então criar um banco de dados separado para esse funcionário.

Após a criação da tabela, deveremos entregar algumas queries prontas para que sejam enviadas para o programador. As queries são as seguintes:
1 – Trazer todos os dados.
2 – Trazer o nome do livro e o nome da editora
3 – Trazer o nome do livro e a UF dos livros publicados por autores do sexo masculino.
4 - Trazer o nome do livro e o número de páginas dos livros publicados por autores do sexo feminino.
5 – Trazer os valores dos livros das editoras de São Paulo.
6 – Trazer os dados dos autores do sexo masculino que tiveram livros publicados por São Paulo ou Rio de Janeiro

* Modelagem Básica 

/* Modelo Conceitual - 

CLIENTE

NOME - CARACTER(30)
CPF - NUMERICO(11)
EMAIL - CARACTER(30)
TELEFONE - CARACTER(30)
ENDERECO - CARACTER(100)
SEXO - CARACTER(1)

/* Modelo logico - 

![Captura de tela 2024-02-05 204956](https://github.com/JulioMancini/Banco-de-Dados-e-SQL/assets/145502330/bd0ddf24-cca5-405e-b86d-dc4f452bb419)

* MODELAGEM FÍSICA - SCRIPTS DE BANCO

```CREATE DATABASE PROJETO;```

```USE PROJETO;```

```
CREATE TABLE CLIENTE(
	NOME VARCHAR(30),
	SEXO CHAR(1),
	EMAIL VARCHAR(30),
	CPF INT(11),
	TELEFONE VARCHAR(30),
	ENDERECO VARCHAR(100);
```
```
DESC CLIENTE;
```

![2](https://github.com/JulioMancini/Banco-de-Dados-e-SQL/assets/145502330/85138e5d-d37b-4bdf-b87d-67ff7db54128)

* Tipos de dados

Todos os banos de dados possuem tipos que devem ser atribuidos aos dados de uma tabela.
Para caracteres literais, temos char e varchar, para números temos int e float, para
objetos como fotos e documentos, temos o blob, para textos extensos, temos o text. 
A disciplina de banco de dados é tão fantástica que ao entendermos o porque das coisas,
podemos iniciar já em modo avançado e um bom exemplo disso são os tipos. Há uma profissão
dentro da área que é a do analista de performance ou tuning, esse profissional é responsável
por analisar o banco de dados e deixá-lo mais rápido. Parece algo avançado, e é! Porém,
com alguas atitudes simples, podemos deixar o banco sem a necessidade de atuação desse profissional.

Cada caracter no banco de dados, vale 1 byte. Sendo assim, se eu entro com o dado JOÃO,
estou entrando com 4 bytes no meu banco. E o que isso tem a ver com a tiagem de tabelas?

O banco de dados funciona como um download de dados da internet. Se baixamos um arquivo de 1 giga,
temos um temo maior que o download de 50 megas, considerando a mesma velocidade de conexão.

Ao tiparmos uma tabela de modo errado ou displicente, vamos aumentar a quantidade de dados que 
será baixada do banco de dados, prolongando assim o tempo de resposta.

Uma comparacao bem didatica é o tipo char e varchar
A palavra var, vem de variant, em ingles, ou seja, que é dinâmica. Logo, vimos que 1 caracter
é igual a 1 byte. Vejamos então a tipagem

varchar(10)
char(10)

entrando a palavra joao

total de bytes varchar(10) = 4 bytes
toal de bytes cahr(10) = 10 bytes

isso ocorre pois o char não varia. Os caracteres restantes serao preenchidos com espaço. 
eles nao ficam vazios. Enquanto que no varchar, o tipo varia conforme o dado.
Entao utilizo sempre o varchar? Não. O charé ligeiramente mais performatico, por nao
ter que gastar tempo variando de tamanho. Entao a regra é utilizar sempre o char quando
sabemos que o numero de caracteres naquela coluna nao vai variar nunca. Por exemplo,
unidade federativa, com dois digitos, sexo com um digito e assim por diante. Vista a diferença
que podemos fazer com uma tipagem correta de tabelas, na próxima aula detalharemos os tipos do mysql
e nos modulos específicos de cada banco, você entenderá os tipos correspondentes no sql server
e no oracle, que mudam muito pouco.

*  Inserindo dados e valores nulos

```USE PROJETO;```

/* FORMA 01 - OMITINDO AS COLUNAS */

```
INSERT INTO CLIENTE VALUES('JOAO','M','JOAO@GMAIL.COM',988638273,'22923110','MAIA LACERDA - ESTACIO - RIO DE JANEIRO - RJ');
```

```
INSERT INTO CLIENTE VALUES('CELIA','F','CELIA@GMAIL.COM',541521456,'25078869','RIACHUELO - CENTRO - RIO DE JANEIRO - RJ');
```

```
INSERT INTO CLIENTE VALUES('JORGE','M',NULL,885755896,'58748895','OSCAR CURY - BOM RETIRO - PATOS DE MINAS - MG');
```

/* FORMA 02 - COLOCANDO AS COLUNAS */

```
INSERT INTO CLIENTE(NOME,SEXO,ENDERECO,TELEFONE,CPF) VALUES('LILIAN','F','SENADOR SOARES - TIJUCA - RIO DE JANEIRO - RJ','947785696',887774856);
```

/* FORMA 03 - INSERT COMPACTO - SOMENTE MYSQL */

```
INSERT INTO CLIENTE VALUES('ANA','F','ANA@GLOBO.COM',85548962,'548556985','PRES ANTONIO CARLOS - CENTRO - SAO PAULO - SP'),('CARLA','F','CARLA@TERATI.COM.BR',7745828,'66587458','SAMUEL SILVA - CENTRO - BELO HORIZONTE - MG');
```

![3](https://github.com/JulioMancini/Banco-de-Dados-e-SQL/assets/145502330/57ed7c0d-6ea7-4077-9010-b3dc52053afa)

/* O COMANDO SELECT 
selecao projecao e juncao
*/

SELECT NOW() as DATA_HORA, 'JULIO LEAO' AS ENGdados;

SELECT 'JULIO LEAO';

SELECT 'BANCO DE DADOS';

/* ALIAS DE COLUNAS */


SELECT NOME AS CLIENTE, SEXO, EMAIL FROM CLIENTE;

SELECT NOME, SEXO, EMAIL, ENDERECO FROM CLIENTE;

SELECT   EMAIL, SEXO, ENDERECO, NOME FROM CLIENTE;

SELECT   EMAIL, SEXO, ENDERECO, NOME, NOW() AS DATA_HORA FROM CLIENTE;

/* APENAS PARA FINS ACADEMICOS */

SELECT * FROM CLIENTE;

/*TABELA ERRADA - NAO DIGITE DIRETAMENTE NO BANCO */
CREATE TABLE CLIENTE(
	NOME VARCHAR(30),
	SEXO CHAR(1),
	EMAIL VARCHAR(30)
	CPF INT(11),
	TELEFONE VARCHAR(30),
	ENDERECO VARCHAR(100),

);

SELECT * FROM CLIENTE;


/* FILTRANDO DADOS COM WHERE E LIKE */

SELECT NOME, TELEFONE FROM CLIENTE;

/* FILTRANDO */

SELECT NOME, SEXO FROM CLIENTE
WHERE SEXO = 'M';

SELECT NOME, ENDERECO FROM CLIENTE
WHERE SEXO = 'F';

SELECT NOME, SEXO FROM CLIENTE
WHERE ENDERECO = 'RJ';

/* UTILIZANDO O LIKE */

SELECT NOME, SEXO FROM CLIENTE
WHERE ENDERECO LIKE 'RJ';

/* CARACTER CORINGA % -> QUALQUER COISA */

SELECT NOME, SEXO FROM CLIENTE
WHERE ENDERECO LIKE '%RJ';

SELECT NOME, SEXO, ENDERECO FROM CLIENTE
WHERE ENDERECO LIKE '%RJ';

SELECT NOME, SEXO, ENDERECO FROM CLIENTE
WHERE ENDERECO LIKE 'OSCAR CURY%';

SELECT NOME, SEXO, ENDERECO FROM CLIENTE
WHERE ENDERECO LIKE '%CENTRO%';

* Resolvendo o exercício de negócio simples

O cliente Tera Comércio de Produtos S.A, solicitou a modelagem de um banco de dados para cadastro dos seus clientes.
A função da Unidados é a análise dos requisitos junto aos usuários para a correta construção do produto. O cliente deseja que inicialmente os scripts sejam construídos para o Banco de Dados MySQL, porém, posteriormente pode haver mudança no ambiente e consequentemente adaptação dos scripts para outros produtos de SGBD.
O cliente não quer nenhuma informação relativa à vendas ou estoque, desejando somente as informações primárias de Clientes.

O nosso cliente solicitou uma tabela para armazenar os livros que são comercializados pela empresa. A solicitação é somente para livros e não há a necessidade de realizar busca em outras tabelas. Hoje há um funcionário de vendas que tem uma tabela do Excel para guardar esses registros, mas as buscas estão ficando complexas. Decidiu-se então criar um banco de dados separado para esse funcionário.
Após a criação da tabela, deveremos entregar algumas queries prontas para que sejam enviadas para o programador. As queries são as seguintes:

1. Trazer todos os dados.
2. Trazer o nome do livro e o nome da editora
3. Trazer o nome do livro e a UF dos livros publicados por autores do sexo masculino.
4. Trazer o nome do livro e o número de páginas dos livros publicados por autores do sexo feminino.
5. Trazer os valores dos livros das editoras de São Paulo.
6. Trazer os dados dos autores do sexo masculino que tiveram livros publicados por São Paulo ou Rio de Janeiro


`CREATE DATABASE LIVRARIA;`

`USE LIVRARIA;`

```
CREATE TABLE LIVROS(
	LIVRO VARCHAR(100),
	AUTOR VARCHAR(100),
	SEXO CHAR(1),
	PAGINAS INT(5),
	EDITORA VARCHAR(30),
	VALOR FLOAT(10,2),
	UF CHAR(2),
	ANO INT(4)
);
```

/* VERIFICANDO OS BANCOS */
SHOW DATABASES;

/* CONEVCTANDO A UM BANCO */
USE LIVRARIA;

```
INSERT INTO LIVROS VALUES('Cavaleiro Real','Ana Claudia','F',465,'Atlas',49.9,'RJ',2009);
INSERT INTO LIVROS VALUES('SQL para leigos','João Nunes','M',450,'Addison',98,'SP',2018);
INSERT INTO LIVROS VALUES('Receitas Caseiras','Celia Tavares','F',210,'Atlas',45,'RJ',2008);
INSERT INTO LIVROS VALUES('Pessoas Efetivas','Eduardo Santos','M',390,'Beta',78,'RJ',2018);
INSERT INTO LIVROS VALUES('Habitos Saudáveis','Eduardo Santos','M',630,'Beta',150,'RJ',2019);
INSERT INTO LIVROS VALUES('A Casa Marrom','Hermes Macedo','M',250,'Bubba',60,'MG',2016);
INSERT INTO LIVROS VALUES('Estacio Querido','Geraldo Francisco','M',310,'Insignia',100,'ES',2015);
INSERT INTO LIVROS VALUES('Pra sempre amigas','Leda Silva','F',510,'Insignia',78,'ES',2011);
INSERT INTO LIVROS VALUES('Copas Inesqueciveis','Marco Alcantara','M',200,'Larson',130,'RS',2018);
INSERT INTO LIVROS VALUES('O poder da mente','Clara Mafra','F',120,'Continental',56,'SP',2017);
```

/*1 – Trazer todos os dados.*/

`select *
from livros;
`

/*2 – Trazer o nome do livro e o nome da editora*/

`
SELECT LIVRO, EDITORA
FROM LIVROS;
`


/*3 – Trazer o nome do livro e a UF dos livros publicados por autores do sexo masculino.*/

`SELECT LIVRO, UF
FROM LIVROS
WHERE SEXO = 'M';`

SELECT AUTOR, SEXO,LIVRO, UF

`FROM LIVROS
WHERE SEXO = 'M';`

/*4 - Trazer o nome do livro e o número de páginas dos livros publicados por autores do sexo feminino.*/

`SELECT LIVRO, PAGINAS
FROM LIVROS
WHERE SEXO = 'F';`


`SELECT AUTOR,  LIVRO, PAGINAS
FROM LIVROS
WHERE SEXO = 'F';`


/*5 – Trazer os valores dos livros das editoras de São Paulo.*/

`SELECT LIVRO, VALOR
FROM LIVROS
WHERE UF = 'SP';`


`SELECT UF, LIVRO, VALOR
FROM LIVROS
WHERE UF = 'SP';`

/*6 – Trazer os dados dos autores do sexo masculino que tiveram livros publicados por São Paulo ou Rio de Janeiro (Questão Desafio).*/

`SELECT AUTOR, SEXO, UF
FROM LIVROS
WHERE SEXO = 'M'
AND UF = 'SP'
OR UF = 'RJ';`


`SELECT AUTOR, SEXO, UF
FROM LIVROS
WHERE 
SEXO = 'M' AND (UF = 'SP' OR UF = 'RJ');`


`SELECT AUTOR, SEXO, UF
FROM LIVROS
WHERE SEXO = 'M'
AND UF = 'SP'
AND paginas > 100;`

/* OPERADORES LÓGICOS 
OR -> PARA QUE A SAIDA DA QUERY SEJA VERDADEIRA, BASTA QUE APENAS UMA CONDICAO SEJA VERDADEIRA.
AND -> PARA QUE A SAIDA SEJA VERDADEIRA TODAS AS CONDICOES PRECISAM SER VERDADEIRAS.
*/

/* OR - OU */

`SHOW DATABASES;`

`USE PROJETO;`

`SELECT * FROM CLIENTE;`

`SELECT NOME, SEXO, ENDERECO FROM CLIENTE
WHERE 
SEXO = 'M' OR ENDERECO LIKE '%RJ';`

`SELECT NOME, SEXO, ENDERECO FROM CLIENTE
WHERE 
SEXO = 'M' AND ENDERECO LIKE '%RJ';`

`SELECT NOME, SEXO, ENDERECO  FROM CLIENTE
WHERE
SEXO = 'F' OR ENDERECO LIKE '%ESTACIO';`

/* AND - E */

`SELECT NOME, SEXO, ENDERECO  FROM CLIENTE
WHERE 
SEXO = 'M' AND ENDERECO LIKE '%RJ';`

`SELECT NOME, SEXO, ENDERECO FROM CLIENTE
WHERE
SEXO = 'F' AND ENDERECO LIKE '%ESTACIO';`

/* COUNT(*), GROUP BY, PERFORMANCE COM OPERADORES
LOGICOS */

/* CONTANDO OS REGISTROS DE UMA TABELA */

`SELECT COUNT(*) AS "Quantidade de Registros da Tab. Cliente"
 FROM CLIENTE;`

/* OPERADOR GROUP BY */

`SELECT SEXO, COUNT(*)
FROM CLIENTE;`

`SELECT * FROM CLIENTE;`

`SELECT SEXO, COUNT(*) 
FROM CLIENTE
GROUP BY SEXO;`

/* PERFORMANCE EM OPERADORES LOGICOS */

/* 1 MILHAO DE REGISTROS

/*PARA CONTAR

`SELECT COUNT(*) FROM CLIENTE;`

`SELECT SEXO, COUNT(*) FROM CLIENTE
GROUP BY SEXO;`

`SELECT CIDADE, COUNT(*) FROM CLIENTE
GROUP BY CIDADE;`

/*CONDICAO
SEXO = F
CIDADE = RIO DE JANEIRO

/*SITUACAO - TRATANDO COM OU / OR

70% MULHERES = SEXO = F
30% MORA NO RIO DE JANEIRO

`SELECT NOME, SEXO, ENDERECO
FROM CLIENTE
WHERE SEXO = 'F'
OR CIDADE = 'RIO DE JANEIRO';`

/*SITUACAO - TRATANDO COM E / AND

70% MULHERES = SEXO = F
30% MORA NO RIO DE JANEIRO

`SELECT NOME, SEXO, ENDERECO
FROM CLIENTE
WHERE CIDADE = 'RIO DE JANEIRO'
AND SEXO = 'F';`
