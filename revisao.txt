Gabarito Atividade 8 - 1ª Etapa: Revisão Prova Final

Exercício 1
Faça uma junção entre as tabelas “ALUNOS”, “NOTAS” e “DISCIPLINAS” trazendo as colunas de nome da disciplina, nome do aluno e turma.

SELECT A.NOME, A.TURMA, D.NOME_DISCIPLINA
FROM ALUNOS AS A
INNER JOIN NOTAS AS N 
ON A.MATRICULA = N.MATRICULA
INNER JOIN DISCIPLINAS AS D
ON N.COD_DISCIPLINA =  D.COD_DISCIPLINA;

Exercício 2
A partir da junção realizada no exercício 1, faça uma consulta que traga a quantidade de alunos por disciplina.

SELECT D.NOME_DISCIPLINA, COUNT(A.MATRICULA) AS QUANTIDADE
FROM ALUNOS AS A 
INNER JOIN NOTAS AS N
ON A.MATRICULA = N.MATRICULA 
INNER JOIN DISCIPLINAS AS D 
ON N.COD_DISCIPLINA = D.COD_DISCIPLINA 
GROUP BY D.NOME_DISCIPLINA; 

Exercício 3
A partir da consulta realizada no exercício 2, faça uma consulta que traga os nomes das disciplinas que têm mais de 7 alunos.

SELECT D.NOME_DISCIPLINA
FROM ALUNOS AS A 
INNER JOIN NOTAS AS N
ON A.MATRICULA = N.MATRICULA 
INNER JOIN DISCIPLINAS AS D 
ON N.COD_DISCIPLINA = D.COD_DISCIPLINA 
GROUP BY D.NOME_DISCIPLINA
HAVING COUNT(A.MATRICULA) > 7; 

Exercício 4
Crie uma consulta que retorne a quantidade de estudantes existentes na base de dados.

SELECT COUNT(MATRICULA) AS TOTAL 
FROM ALUNOS;

Exercício 5
Observe o diagrama a seguir e responda o que se pede.



Suponha que em um banco de dados de uma loja há as duas tabelas que estão no diagrama acima. 
Foi solicitada a criação de uma nova tabela que permita registrar os produtos dos pedidos. Analise o diagrama acima e pense: com quais outras entidades essa nova tabela deverá se relacionar? Ela será uma entidade fraca (dependente)? Quais são suas chaves? Quais dados ela deve guardar? Quais são os tipos de dados de cada coluna?

CREATE TABLE PRODUTO (
	ID_PRODUTO INT PRIMARY KEY NOT NULL,
	PRECO FLOAT,
	NOME_PROD VARCHAR(200),
	DESCRICAO VARCHAR(500)
)

Foi criada uma nova tabela para registrar apenas os dados de acesso ao sistema dos usuários. Por isso, você deve alterar a tabela “CLIENTE” para que as colunas “USUARIO” e “SENHA” sejam deletadas.

	ALTER TABLE CLIENTE
	DROP COLUMN USUARIO;

	ALTER TABLE CLIENTE
	DROP COLUMN SENHA;

Na tabela de “CLIENTE” deve ser inserida uma nova coluna que vai receber o endereço de email 

	ALTER TABLE CLIENTE
	ADD COLUMN EMAIL VARCHAR(150);


