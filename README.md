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

# Modelagem na prática

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


