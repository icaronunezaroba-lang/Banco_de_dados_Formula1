Banco de Dados Fórmula 1 (MySQL)

Script SQL em MySQL que modela um banco de dados simples sobre a Fórmula 1: países, equipes, corridas (Grandes Prêmios), pilotos e a participação dos pilotos nas corridas. Desenvolvido como exercício prático de modelagem de dados e consultas SQL.

 Sobre o projeto

O script cria o banco db_formula1, define as tabelas com suas chaves primárias e estrangeiras, popula os dados e resolve uma lista de exercícios com SELECT, INSERT, ALTER TABLE, UPDATE, GROUP BY e funções de agregação.

Todos os nomes de pilotos são fictícios, criados apenas para fins didáticos.

 Estrutura do banco
Tabela	Descrição	Chave primária
td_paises	Países (código e nome)	codigo
td_equipes	Equipes e o país de origem	sigla
td_corridas	Grandes Prêmios, país sede e quantidade de voltas	sigla_gp
td_pilotos	Pilotos, país, equipe e salário	numero
td_participantes	Participação de cada piloto em cada corrida (posição de largada)	(sigla_gp, num_piloto)
Relacionamentos
td_equipes.cod_pais → td_paises.codigo
td_corridas.cod_pais → td_paises.codigo
td_pilotos.cod_pais → td_paises.codigo
td_pilotos.sigla_equipe → td_equipes.sigla
td_participantes.sigla_gp → td_corridas.sigla_gp
td_participantes.num_piloto → td_pilotos.numero

Exercícios resolvidos
Nº	Descrição
1	Inserção de 10 novos pilotos (números 21 a 30)
3	Países cujo nome começa com B e termina com l (LIKE)
4	Pilotos do Brasil, Itália ou França (IN)
5	Listagem do nome de todos os pilotos
6	Grandes Prêmios e quantidade de voltas (com AS)
7	Nome e país dos pilotos (com alias)
8	Inclusão da coluna salario em td_pilotos (ALTER TABLE)
9	Preenchimento dos salários (UPDATE)
10	Pilotos com salário entre 70 mil e 100 mil (BETWEEN)
11	Média salarial por país (AVG + GROUP BY)
12	Salários distintos em ordem crescente (DISTINCT + ORDER BY)
 Exemplos de consultas

1. Pilotos de países específicos

sql
SELECT nome AS 'Nome'
FROM td_pilotos
WHERE cod_pais IN ('BRA', 'ITA', 'FRA');

2. Faixa salarial

sql
SELECT nome
FROM td_pilotos
WHERE salario BETWEEN 70000 AND 100000;

3. Média salarial por país

sql
SELECT cod_pais AS 'País', ROUND(AVG(salario), 2) AS 'Média Salarial'
FROM td_pilotos
GROUP BY cod_pais;
 Como executar

Pré-requisitos: MySQL 8+ (ou MariaDB) e um cliente como MySQL Workbench, DBeaver ou o terminal.

Clone o repositório:
bash
   git clone https://github.com/SEU-USUARIO/NOME-DO-REPOSITORIO.git
   cd NOME-DO-REPOSITORIO
Execute o script pelo terminal:
bash
   mysql -u seu_usuario -p < formula1.sql

Ou abra o arquivo formula1.sql no MySQL Workbench e execute tudo (⚡). 3. Selecione o banco e consulte:

sql
   USE db_formula1;
   SELECT * FROM td_pilotos;
🛠️ Tecnologias
MySQL
SQL (DDL, DML e DQL)
Git e GitHub
👤 Autor

Ícaro Rafael Nunes Estudante de Ciência da Computação — UDF Centro Universitário
