create database Z3R0C0D3;
use Z3R0C0D3;

CREATE TABLE Financeiro (
    id_financeiro INTEGER PRIMARY KEY, 
    nomeFuncionario VARCHAR(100),
    cpf CHAR(11)
);

CREATE TABLE Marketing (
    id_colaborador INTEGER PRIMARY KEY, 
    id_patrocinador INTEGER,
    cargo CHAR(40),                    
    nome VARCHAR(100),
    cpf CHAR(11),
    fk_Financeiro_id_financeiro INTEGER,
    FOREIGN KEY (fk_Financeiro_id_financeiro) REFERENCES Financeiro(id_financeiro) 
);


CREATE TABLE Patrocinador (
    id_patrocinador INTEGER PRIMARY KEY,
    nome VARCHAR(100),
    cnpj CHAR(14),
    fk_Marketing_id_colaborador INTEGER,
    dataContrato DATE,
    valor DECIMAL(12, 2),               
    FOREIGN KEY (fk_Marketing_id_colaborador) REFERENCES Marketing(id_colaborador)
);

CREATE TABLE Equipe (
    id_equipe INTEGER PRIMARY KEY,
    nome VARCHAR(50),
    fk_Marketing_id_colaborador INTEGER,
    FOREIGN KEY (fk_Marketing_id_colaborador) REFERENCES Marketing(id_colaborador)
);

CREATE TABLE Patrocina (
    fk_Equipe_id_equipe INTEGER,
    fk_Patrocinador_id_patrocinador INTEGER,
    dataInicio DATE,
    dataFim DATE,
    PRIMARY KEY (fk_Equipe_id_equipe, fk_Patrocinador_id_patrocinador),
    FOREIGN KEY (fk_Equipe_id_equipe) REFERENCES Equipe(id_equipe),
    FOREIGN KEY (fk_Patrocinador_id_patrocinador) REFERENCES Patrocinador(id_patrocinador)
);

CREATE TABLE Torneio (
    id_torneio INTEGER PRIMARY KEY,
    dataInicio DATE,
    dataFim DATE,
    bonificacao DECIMAL(10, 2),
    nomeTorneio VARCHAR(100),
    nomeJogo VARCHAR(100),
    fk_Equipe_id_equipe INTEGER,
    FOREIGN KEY (fk_Equipe_id_equipe) REFERENCES Equipe(id_equipe)
);

CREATE TABLE Jogador (
    id_jogador INTEGER PRIMARY KEY,
    nome VARCHAR(100),
    idade INTEGER,
    sexo CHAR(1),                         
    cpf CHAR(11),
    funcao VARCHAR(40), 
    salario DECIMAL (10,2),
    status CHAR(1),         
    fk_Equipe_id_equipe INTEGER,
    FOREIGN KEY (fk_Equipe_id_equipe) REFERENCES Equipe(id_equipe)
);

CREATE TABLE Disputa (
    fk_Jogador_id_jogador INTEGER,
    fk_Torneio_id_torneio INTEGER,
    PRIMARY KEY (fk_Jogador_id_jogador, fk_Torneio_id_torneio),
    FOREIGN KEY (fk_Jogador_id_jogador) REFERENCES Jogador(id_jogador),
    FOREIGN KEY (fk_Torneio_id_torneio) REFERENCES Torneio(id_torneio)
);

CREATE TABLE Partida (
    id_partida INTEGER PRIMARY KEY,
    data DATE,
    fase VARCHAR(40),                      -- Ex: Quartas, Semis, Final
    resultado CHAR(1),                     -- Ex: V = Vitória, D = Derrota
    fk_Torneio_id_torneio INTEGER,
    FOREIGN KEY (fk_Torneio_id_torneio) REFERENCES Torneio(id_torneio)
);

CREATE TABLE Joga (
    fk_Jogador_id_jogador INTEGER,
    fk_Partida_id_partida INTEGER,
    tempoJogado TIME,
    PRIMARY KEY (fk_Jogador_id_jogador, fk_Partida_id_partida),
    FOREIGN KEY (fk_Jogador_id_jogador) REFERENCES Jogador(id_jogador),
    FOREIGN KEY (fk_Partida_id_partida) REFERENCES Partida(id_partida)
);

CREATE TABLE Estatisticas (
    id_estatisticas INTEGER PRIMARY KEY auto_increment,
    eliminacoes INTEGER,
    assistencias INTEGER,
    dano INTEGER,
    dano_bloqueado INTEGER,
    cura INTEGER,
    mortes INTEGER,
    avaliacaoTecnica FLOAT,
    duracao TIME,
    id_jogador INTEGER,
    id_partida INTEGER,
    FOREIGN KEY (id_jogador) REFERENCES Jogador(id_jogador),
    FOREIGN KEY (id_partida) REFERENCES Partida(id_partida)
);

INSERT INTO Marketing (id_colaborador, id_patrocinador, cargo, nome, cpf) VALUES 
(1, 1, 'Gerente', 'Ana Torres', '12345678901'), 
(2, 2, 'Analista', 'Carlos Lima', '98765432100');
INSERT INTO Patrocinador (id_patrocinador, nome, cnpj, fk_Marketing_id_colaborador, dataContrato, valor) VALUES
(1, 'RedBull Gaming', '12345678000199', 1, '2024-01-01', 50000.00), 
(2, 'HyperX', '98765432000188', 2, '2024-02-15', 40000.00);
INSERT INTO Equipe (id_equipe, nome, fk_Marketing_id_colaborador) VALUES 
(1, 'Overwatch Elite', 1), 
(2, 'Marvel Rivals Strike', 2);
INSERT INTO Patrocina (fk_Equipe_id_equipe, fk_Patrocinador_id_patrocinador, dataInicio, dataFim) VALUES 
(1, 1, '2024-01-01', '2025-12-31'), 
(2, 2, '2024-02-15', '2025-12-31');
INSERT INTO Torneio (id_torneio, dataInicio, dataFim, bonificacao, nomeJogo, nomeTorneio, fk_Equipe_id_equipe) VALUES 
(1, '2024-03-01', '2025-03-15', 15000.00, 'Overwatch', 'Overwatch League', 1), 
(2, '2024-04-10', '2025-04-25', 18000.00, 'Marvel Rivals', 'Marvel Rivals Cup', 2);
INSERT INTO Partida (id_partida, data, fase, resultado, fk_Torneio_id_torneio) VALUES
(1, '2025-03-05', 'Quartas', 'V', 1), 
(2, '2025-03-05', 'Semis', 'D', 1), 
(3, '2025-04-15', 'Semifinal', 'D', 2);
INSERT INTO Jogador (id_jogador, salario, nome, idade, sexo, cpf, funcao, status, fk_Equipe_id_equipe) VALUES
(1, 5000.00, 'ShadowPulse', 28, 'M', '04332181960', 'Tank', 'A', 1),
(2, 4500.00, 'VortexX', 19, 'M', '38908386379', 'Suporte', 'A', 1),
(3, 4800.00, 'BlitzWolf', 30, 'M', '26542351161', 'Suporte', 'A', 1),
(4, 6000.00, 'CryoNova', 23, 'F', '07816184959', 'DPS', 'A', 1),
(5, 4700.00, 'DarkSniper', 29, 'M', '03413164752', 'Suporte', 'A', 1),
(6, 5200.00, 'OmegaZen', 23, 'M', '41928327648', 'DPS', 'I', 1),
(7, 5100.00, 'ToxicByte', 28, 'F', '03056413953', 'Flex', 'I', 1),
(8, 4400.00, 'FireStrike', 24, 'F', '24238849696', 'Suporte', 'I', 1),
(9, 4800.00, 'N3onPhantom', 21, 'M', '87101226916', 'Flex', 'I', 1),
(10, 4600.00, 'SilentRage', 27, 'F', '84801845146', 'DPS', 'I', 1),
(11, 5300.00, 'IronVenom', 25, 'M', '48281489325', 'DPS', 'A', 2),
(12, 5500.00, 'StarkFlame', 26, 'M', '95701543039', 'Tank', 'A', 2),
(13, 4900.00, 'GhostSpidey', 19, 'F', '18227824896', 'DPS', 'A', 2),
(14, 6000.00, 'WandaHex', 26, 'M', '46578713315', 'Tank', 'A', 2),
(15, 5200.00, 'NovaCrush', 27, 'M', '93010310518', 'DPS', 'A', 2),
(16, 5500.00, 'QuantumFury', 22, 'F', '38299737631', 'Suporte', 'A', 2),
(17, 4900.00, 'StormZero', 28, 'F', '56670106513', 'DPS', 'I', 2),
(18, 4500.00, 'HawkBlink', 21, 'F', '26247317810', 'Tank', 'I', 2),
(19, 4700.00, 'PantherClaw', 19, 'M', '26773602606', 'Suporte', 'I', 2),
(20, 5600.00, 'WidowByte', 30, 'F', '46872343098', 'Tank', 'I', 2);

INSERT INTO Disputa (fk_Jogador_id_jogador, fk_Torneio_id_torneio) VALUES 
(1, 1),
(2, 1),
(3, 1),
(4, 1),
(5, 1),
(6, 1),
(7, 1),
(8, 1),
(9, 1),
(10, 1),
(11, 2),
(13, 2),
(14, 2),
(15, 2),
(16, 2),
(17, 2),
(18, 2),
(19, 2),
(20, 2);

INSERT INTO Joga (fk_Jogador_id_jogador, fk_Partida_id_partida, tempoJogado) VALUES
(1, 1, '00:35:00'), 
(2, 1, '00:35:00'),  
(3, 1, '00:35:00'),  
(4, 1, '00:35:00'), 
(5, 1, '00:35:00'),
(1, 2, '00:30:00'),  
(2, 2, '00:30:00'),  
(3, 2, '00:30:00'),  
(4, 2, '00:30:00'),  
(5, 2, '00:30:00'),
(11, 3, '00:30:00'),  
(12, 3, '00:30:00'),  
(13, 3, '00:30:00'), 
(14, 3, '00:30:00'), 
(15, 3, '00:30:00');

INSERT INTO Estatisticas (id_estatisticas, eliminacoes, assistencias, dano, dano_bloqueado, cura, mortes, avaliacaoTecnica, duracao, id_jogador, id_partida) VALUES
(1, 30, 12, 37000, 892, 0, 7, 8.5, '00:35:00', 1, 1),  
(2, 43, 4, 48000, 0, 0, 5, 10, '00:35:00', 4, 1),  
(3, 38, 3, 39382, 0, 1000, 2, 9.5, '00:35:00', 6, 1), 
(4, 4, 52, 420, 0, 41873,0, 8.8, '00:35:00', 5, 1), 
(5, 11, 47, 18000, 0, 27893, 6, 90, '00:35:00', 3, 1),  
(6, 14, 8, 12000, 25000, 0, 7, 7.8, '00:30:00', 1, 2),
(7, 25,  4, 38000, 0, 0, 5, 7.5, '00:30:00', 4, 2),
(8, 22,  3, 34000, 0, 0, 6, 7.2, '00:30:00', 6, 2),
(9, 3, 40,  2500,  0, 22000, 7, 6.9, '00:30:00', 5, 2),
(10, 5, 35, 2000, 0, 20000, 8, 6.8, '00:30:00', 3, 2), 
(11, 16, 6, 9000, 32000, 0, 6, 7.8, '00:30:00', 12, 3),
(12, 14, 5, 8500, 28000, 0, 7, 7.5, '00:30:00', 14, 3),
(13, 30,  4, 47000, 0, 0, 5, 8.3, '00:30:00', 11, 3),
(14, 27,  5, 44000, 0, 0, 6, 8.0, '00:30:00', 13, 3), 
(15, 4, 40, 2500, 0, 30000, 5, 7.2, '00:30:00', 16, 3),
(16, 3, 35, 2000, 0, 28000, 6, 7.0, '00:30:00', 19, 3);

-- 1) 5 CONSULTAS COM SELECT E WHERE 

SELECT nome, funcao, status
FROM Jogador
WHERE status = 'A'; -- (BUSCAR JOGADORES ATIVOS)

SELECT nome, valor
FROM Patrocinador
WHERE valor > 45000.00; -- (BUSCAR PATROCINADORES COM CONTRATO ACIMA DE 45000 REAIS)

SELECT j.nome, j.funcao
FROM Jogador j
JOIN Equipe e ON j.fk_Equipe_id_equipe = e.id_equipe
WHERE e.nome = 'Overwatch Elite'; -- (BUSCAR JOGADORES DA OVERWATCH ELITE)

SELECT id_partida, data, fase
FROM Partida
WHERE resultado = 'V'; -- (BUSCAR PARTIDAS VENCIDAS)

SELECT id_jogador, id_partida, eliminacoes, avaliacaoTecnica
FROM Estatisticas
WHERE eliminacoes > 20; -- (BUSCAR ESTATÍSTICAS DE JOGADORES COM MAIS DE 20 ELIMINAÇÕES)

-- 2) 5 consultas com GROUP BY e ORDER BY com funções de agregação 

SELECT e.id_jogador, j.nome,
SUM(e.eliminacoes) AS total_eliminacoes
FROM Estatisticas e
JOIN Jogador j  ON j.id_jogador = e.id_jogador
GROUP BY e.id_jogador, j.nome
ORDER BY total_eliminacoes DESC; -- (TOTAL DE ELIMINAÇÕES POR JOGADOR)

SELECT j.funcao,
AVG(e.avaliacaoTecnica) AS media_avaliacao
FROM Estatisticas e
JOIN Jogador j ON j.id_jogador = e.id_jogador
GROUP BY j.funcao
ORDER BY media_avaliacao DESC; -- (MÉDIA DE NOTA POR FUNÇÃO/ROLE)

SELECT e.nome AS equipe,
COUNT(*) AS jogadores_ativos
FROM Equipe e
JOIN Jogador j ON j.fk_Equipe_id_equipe = e.id_equipe
WHERE j.status = 'A'
GROUP BY e.id_equipe, e.nome
ORDER BY jogadores_ativos DESC; -- (NÚMERO DE JOGADORES ATIVOS POR EQUIPE)

SELECT m.nome AS colaborador_marketing,
SUM(p.valor) AS total_patrocinios
FROM Marketing m
JOIN Patrocinador p ON p.fk_Marketing_id_colaborador = m.id_colaborador
GROUP BY m.id_colaborador, m.nome
ORDER BY total_patrocinios DESC; -- (VALOR TOTAL DE PATROCÍNIOS GERENCIADO POR CADA COLABORADOR DE MARKETING)

SELECT t.nomeTorneio,
SUM(es.eliminacoes) AS eliminacoes_totais
FROM Torneio t
JOIN Partida pa ON pa.fk_Torneio_id_torneio = t.id_torneio
JOIN Estatisticas es ON es.id_partida = pa.id_partida
GROUP BY t.id_torneio, t.nomeTorneio
ORDER BY eliminacoes_totais DESC; -- (TOTAL DE ELIMINAÇÕES REGISTRADAS EM CADA TORNEIO)

-- 3) 5 consultas com operadores aritméticos

SELECT p.nome AS patrocinador,
p.valor + t.bonificacao AS total_valor
FROM Patrocinador p
JOIN Patrocina pa ON pa.fk_Patrocinador_id_patrocinador = p.id_patrocinador
JOIN Equipe e ON e.id_equipe = pa.fk_Equipe_id_equipe
JOIN Torneio t ON t.fk_Equipe_id_equipe = e.id_equipe
ORDER BY total_valor DESC; -- (TOTAL DE VALOR DE CONTRATO PARA CADA PATROCINADOR)

SELECT pa.id_partida,
SUM(TIME_TO_SEC(j.tempoJogado)) AS tempo_total_segundos,
SEC_TO_TIME(SUM(TIME_TO_SEC(j.tempoJogado))) AS tempo_total
FROM Joga j
JOIN Partida pa ON pa.id_partida = j.fk_Partida_id_partida
GROUP BY pa.id_partida; -- (TOTAL DE TEMPO DE DE JOGO DE TODOS OS JOGADORES POR PARTIDA)

SELECT j.funcao,
AVG(j.salario) AS salario_medio,
AVG(j.salario) * 12 AS salario_ano
FROM Jogador j
GROUP BY j.funcao
ORDER BY salario_medio DESC; -- (SALÁRIO MÉDIO DOS JOGADORES COM BASE NO TOTAL DE SALÁRIOS POR FUNÇÃO/ROLE)

SELECT m.nome AS colaborador_marketing,
SUM(p.valor) AS total_patrocinios
FROM Marketing m
JOIN Patrocinador p ON p.fk_Marketing_id_colaborador = m.id_colaborador
GROUP BY m.id_colaborador, m.nome
ORDER BY total_patrocinios DESC; -- (VALOR TOTAL DE PATROCÍNIO RESPONSABILIZADO A CADA COLABORADOR/GERENTE DE MARKETING)

SELECT j.nome AS jogador,
AVG(e.eliminacoes) AS media_eliminacoes,
AVG(e.eliminacoes) * COUNT(DISTINCT d.fk_Torneio_id_torneio) AS eliminacoes_por_partida
FROM Estatisticas e
JOIN Jogador j ON e.id_jogador = j.id_jogador
JOIN Disputa d ON e.id_jogador = d.fk_Jogador_id_jogador
GROUP BY j.id_jogador, j.nome; -- (MÉDIA DE ELMINAÇÕES POR JOGADOR)

-- 4) 5 consultas com operadores de comparação

SELECT nome, idade, funcao
FROM Jogador
WHERE idade >= 25;  -- (Jogadores com idade maior ou igual a 25 anos)

SELECT nome, valor
FROM Patrocinador
WHERE valor != 50000.00;  -- (Patrocinadores com valor de contrato diferente de 50000)

SELECT nome, sexo, fk_Equipe_id_equipe
FROM Jogador
WHERE sexo = 'F' AND fk_Equipe_id_equipe = 1;  -- (Jogadores femininas da equipe 'Overwatch Elite')

SELECT id_partida, data, fase
FROM Partida
WHERE data BETWEEN '2025-03-01' AND '2025-04-03';  -- (Partidas entre 2025-03-01 e 2025-04-03)

SELECT nome, funcao
FROM Jogador
WHERE funcao IN ('DPS', 'Tank');  -- (Jogadores com função 'DPS' ou 'Tank')

-- 5) 5 consultas com operadores lógicos (AND, OR)

SELECT nome, funcao, status
FROM Jogador
WHERE status = 'A' AND (funcao = 'DPS' OR funcao = 'Tank');  -- (BUSCAR JOGADORES ATIVOS COM FUNÇÃO 'DPS' OU 'Tank')

SELECT nome, valor, cnpj
FROM Patrocinador
WHERE valor > 45000.00 OR cnpj = '98765432000188'; -- (BUSCAR PATROCINADORES COM CONTRATO ACIMA DE 45000 REAIS OU COM CNPJ '98765432000188')

SELECT nome, idade, salario
FROM Jogador
WHERE (idade BETWEEN 20 AND 30) AND salario > 5000; -- (BUSCAR JOGADORES COM IDADE ENTRE 20 E 30 ANOS E COM SALÁRIO ACIMA DE 5000)

SELECT id_partida, data, fase, resultado
FROM Partida
WHERE resultado = 'V' AND data BETWEEN '2025-03-01' AND '2025-04-30';  -- (BUSCAR PARTIDAS VENCIDAS NO PERÍODO ENTRE 2025-03-01 E 2025-04-30)

SELECT nome, funcao, status, idade
FROM Jogador
WHERE (funcao = 'Suporte' AND status = 'A') OR idade > 30;  -- (BUSCAR JOGADORES COM FUNÇÃO 'Suporte' E STATUS 'A' OU COM IDADE ACIMA DE 30 ANOS)

-- 6) 2 consultas com operadores lógicos e negação (NOT)

SELECT nome, funcao
FROM Jogador
WHERE NOT funcao = 'DPS'; -- (BUSCAR JOGADORES QUE NÃO TÊM FUNÇÃO 'DPS')

SELECT id_partida, data, fase, resultado
FROM Partida
WHERE NOT resultado = 'V'; -- (BUSCAR PARTIDAS QUE NÃO FORAM VENCIDAS)

-- 7) 10 consultas com operadores auxiliares (IS NULL, BETWEEN, LIKE, IN)

SELECT nome, fk_Equipe_id_equipe
FROM Jogador
WHERE fk_Equipe_id_equipe IS NULL; -- (BUSCAR JOGADORES QUE AINDA NÃO ESTÃO VINCULADOS A NENHUMA EQUIPE)

SELECT id_partida, data, fase
FROM Partida
WHERE fk_Torneio_id_torneio IS NULL; -- (BUSCAR PARTIDAS QUE NÃO ESTÃO ASSOCIADAS A NENHUM TORNEIO)

SELECT id_partida, data, fase
FROM Partida
WHERE data BETWEEN '2025-03-01' AND '2025-03-31'; -- (BUSCAR PARTIDAS QUE OCORRERAM NO MÊS DE MARÇO DE 2025)

SELECT nome, salario
FROM Jogador
WHERE salario BETWEEN 4500.00 AND 5500.00; -- (BUSCAR JOGADORES COM SALÁRIOS ENTRE 4500 E 5500 REAIS)

SELECT nome, funcao
FROM Jogador
WHERE nome LIKE 'S%'; -- (BUSCAR JOGADORES CUJOS NOMES COMEÇAM COM A LETRA 'S')

SELECT nome, cnpj
FROM Patrocinador
WHERE nome LIKE '%Gaming%'; -- (BUSCAR PATROCINADORES CUJOS NOMES CONTÊM A PALAVRA 'Gaming')

SELECT nome, cargo
FROM Marketing
WHERE nome LIKE '%a'; -- (BUSCAR COLABORADORES DO MARKETING COM NOMES TERMINANDO EM 'a')

SELECT nome, funcao
FROM Jogador
WHERE funcao IN ('Tank', 'Suporte'); -- (BUSCAR JOGADORES CUJA FUNÇÃO É TANK OU SUPORTE)

SELECT id_jogador, id_partida, eliminacoes, mortes
FROM Estatisticas
WHERE id_jogador IN (1, 4, 11); -- (BUSCAR ESTATÍSTICAS DE JOGADORES COM ID 1, 4 E 11)

SELECT id_jogador, nome
FROM Jogador
WHERE id_jogador NOT IN (
SELECT DISTINCT fk_Jogador_id_jogador FROM Joga
); -- (BUSCAR JOGADORES QUE AINDA NÃO PARTICIPARAM DE NENHUMA PARTIDA)

-- 8) 5 consultas com funções de agregação (SUM, AVG, etc.)

SELECT 
SUM(dano) AS total_dano
FROM
Estatisticas; -- (SOMA TOTAL DE DANO CAUSADO POR TODOS OS JOGADORES EM TODAS AS PARTIDAS)

SELECT AVG(avaliacaoTecnica) AS media_avaliacao_tecnica
FROM Estatisticas; -- (MÉDIA GERAL DE AVALIAÇÃO TÉCNICA DOS JOGADORES)

SELECT MAX(eliminacoes) AS max_eliminacoes
FROM Estatisticas; -- (MAIOR NÚMERO DE ELIMINAÇÕES REGISTRADO EM UMA PARTIDA)

SELECT MIN(salario) AS menor_salario
FROM Jogador
WHERE status = 'A'; -- (MENOR SALÁRIO ENTRE JOGADORES ATIVOS)

SELECT COUNT(*) AS total_partidas
FROM Partida; -- (TOTAL DE PARTIDAS CADASTRADAS NO SISTEMA)

-- 9) 5 consultas com funções de datas (NOW, DATE, YEAR, etc.)

SELECT nome, dataContrato, valor
FROM Patrocinador
WHERE dataContrato < NOW(); -- (PATROCINADORES CUJOS CONTRATOS FORAM FIRMADOS ANTES DA DATA ATUAL)

SELECT nomeTorneio, dataInicio
FROM Torneio
WHERE YEAR(dataInicio) = 2024; -- (TORNEIOS QUE COMEÇARAM NO ANO DE 2024)

SELECT id_partida, data, fase
FROM Partida
WHERE MONTH(data) = 3; -- (PARTIDAS QUE ACONTECERAM EM MARÇO, INDEPENDENTE DO ANO)

SELECT j.nome, p.data, p.fase
FROM Jogador j
JOIN Joga jo ON j.id_jogador = jo.fk_Jogador_id_jogador
JOIN Partida p ON p.id_partida = jo.fk_Partida_id_partida
WHERE DATE(p.data) = '2025-03-05'; -- (JOGADORES QUE JOGARAM EM 05 DE MARÇO DE 2025)

SELECT nomeTorneio, DATEDIFF(dataFim, dataInicio) AS duracao_dias
FROM Torneio; -- (DURAÇÃO DE CADA TORNEIO EM DIAS)

-- 10) 10 sub-consultas com agrupamento e união de dados

SELECT j.nome, e.eliminacoes
FROM Estatisticas e
JOIN Jogador j ON j.id_jogador = e.id_jogador
WHERE e.eliminacoes > (
    SELECT AVG(eliminacoes) FROM Estatisticas
); -- (LISTA JOGADORES QUE TIVERAM MAIS ELIMINAÇÕES DO QUE A MÉDIA GERAL)

SELECT nome
FROM Equipe
WHERE id_equipe IN (
SELECT fk_Equipe_id_equipe
FROM Jogador
WHERE status = 'A'
GROUP BY fk_Equipe_id_equipe
HAVING COUNT(*) > 3
); -- (RETORNA OS NOMES DAS EQUIPES QUE TÊM MAIS DE 3 JOGADORES ATIVOS)

SELECT nome
FROM Jogador
WHERE id_jogador = (
SELECT id_jogador
FROM Estatisticas
GROUP BY id_jogador   
ORDER BY AVG(avaliacaoTecnica) DESC
LIMIT 1
); -- (MOSTRA O JOGADOR COM A MAIOR MÉDIA DE AVALIAÇÃO TÉCNICA)

SELECT nomeTorneio
FROM Torneio
WHERE id_torneio IN (
SELECT pa.fk_Torneio_id_torneio
FROM Estatisticas es
JOIN Partida pa ON pa.id_partida = es.id_partida
GROUP BY pa.fk_Torneio_id_torneio
HAVING SUM(es.eliminacoes) > 100
); -- (RETORNA OS TORNEIOS ONDE A SOMA DO TOTAL DE ELIMINAÇÕES FOI MAIOR QUE 100)

SELECT nome
FROM Jogador
WHERE id_jogador IN (
SELECT fk_Jogador_id_jogador
FROM Joga
GROUP BY fk_Jogador_id_jogador
HAVING COUNT(*) > 1
); -- (LISTA JOGADORES QUE ATUARAM EM MAIS DE UMA PARTIDA)

-- 11) 5 consultas com JOIN e visualização de tabelas

SELECT j.nome AS jogador, e.nome AS equipe
FROM Jogador j
JOIN Equipe e ON j.fk_Equipe_id_equipe = e.id_equipe; -- (EXIBE O NOME DOS JOGADORES E O NOME DA EQUIPE A QUE PERTENCEM)

SELECT p.id_partida, t.nomeTorneio, p.fase, p.resultado
FROM Partida p
JOIN Torneio t ON p.fk_Torneio_id_torneio = t.id_torneio; -- (MOSTRA CADA PARTIDA, A QUAL TORNEIO PERTENCE, A FASE E O RESULTADO)

SELECT j.nome AS jogador, p.id_partida, e.eliminacoes, e.assistencias, e.avaliacaoTecnica
FROM Estatisticas e
JOIN Jogador j ON j.id_jogador = e.id_jogador
JOIN Partida p ON p.id_partida = e.id_partida; -- (LISTA JOGADORES COM ESTATÍSTICAS DETALHADAS POR PARTIDA)

SELECT eq.nome AS equipe, pt.nome AS patrocinador, pt.valor
FROM Patrocina pa
JOIN Equipe eq ON pa.fk_Equipe_id_equipe = eq.id_equipe
JOIN Patrocinador pt ON pa.fk_Patrocinador_id_patrocinador = pt.id_patrocinador; -- (MOSTRA AS EQUIPES E SEUS RESPECTIVOS PATROCINADORES COM O VALOR DO CONTRATO)

SELECT m.nome AS colaborador, p.nome AS patrocinador, p.valor
FROM Marketing m
JOIN Patrocinador p ON m.id_colaborador = p.fk_Marketing_id_colaborador; -- (EXIBE OS COLABORADORES DE MARKETING QUE GERENCIAM CADA PATROCINADOR E O VALOR DO CONTRATO)

-- 12) 10 consultas com tipos de JOIN: INNER, LEFT, RIGHT

SELECT j.nome AS jogador, e.nome AS equipe
FROM Jogador j
INNER JOIN Equipe e ON j.fk_Equipe_id_equipe = e.id_equipe; -- (MOSTRA APENAS JOGADORES QUE ESTÃ VINCULADOS A UMA EQUIPE)

SELECT j.nome, p.id_partida, es.eliminacoes, es.mortes
FROM Estatisticas es
INNER JOIN Jogador j ON es.id_jogador = j.id_jogador
INNER JOIN Partida p ON es.id_partida = p.id_partida; -- (LISTA APENAS OS JOGADORES QUE POSSUEM ESTATÍSTICAS REGISTRADAS EM PARTIDAS)

SELECT t.nomeTorneio, e.nome AS equipe
FROM Torneio t
INNER JOIN Equipe e ON t.fk_Equipe_id_equipe = e.id_equipe; -- (TORNEIOS COM EQUIPES RELACIONADAS)

SELECT e.nome AS equipe, p.nome AS patrocinador
FROM Equipe e
LEFT JOIN Patrocina pa ON e.id_equipe = pa.fk_Equipe_id_equipe
LEFT JOIN Patrocinador p ON p.id_patrocinador = pa.fk_Patrocinador_id_patrocinador; -- (MOSTRA TODAS AS EQUIPES, MESMO AQUELAS SEM PATROCÍNIO)

SELECT m.nome AS colaborador, p.nome AS patrocinador
FROM Marketing m
LEFT JOIN Patrocinador p ON m.id_colaborador = p.fk_Marketing_id_colaborador; -- (MOSTRA TODOS OS COLABORADORES, COM OU SEM PATROCINADOR ASSOCIADO)

SELECT j.nome, es.eliminacoes, es.avaliacaoTecnica
FROM Jogador j
LEFT JOIN Estatisticas es ON j.id_jogador = es.id_jogador; -- (MOSTRA TODOS OS JOGADORES, MESMO OS QUE AINDA NÃO POSSUEM ESTATÍSTICAS REGISTRADAS)

SELECT j.nome, p.id_partida
FROM Jogador j
RIGHT JOIN Joga jo ON j.id_jogador = jo.fk_Jogador_id_jogador
RIGHT JOIN Partida p ON jo.fk_Partida_id_partida = p.id_partida; -- (MOSTRA, TODAS AS PARTIDAS, INCLUINDO AS QUE PODEM NÃO TER JOGADOR VINCULADO AINDA)

SELECT m.nome AS colaborador, p.nome AS patrocinador
FROM Marketing m
RIGHT JOIN Patrocinador p ON p.fk_Marketing_id_colaborador = m.id_colaborador; -- (GARANTE QUE TODOS OS PATROCINADORES SEJAM EXIBIDOS, MESMO SEM COLABORADOR VINCULADO (CASO EXISTA).

SELECT e.nome AS equipe, t.nomeTorneio
FROM Equipe e
RIGHT JOIN Torneio t ON t.fk_Equipe_id_equipe = e.id_equipe; -- (MOSTRA TODOS OS TORNEIOS, MESMO SE ALGUMA EQUIPE NÃO ESTIVER VINCULADA DIRETAMENTE)

SELECT j.nome, jo.tempoJogado
FROM Jogador j
LEFT JOIN Joga jo ON j.id_jogador = jo.fk_Jogador_id_jogador
ORDER BY jo.tempoJogado IS NULL DESC; -- (MOSTRA TODOS OS JOGADORES, DESTACANDO OS QUE AINDA NÃO JOGARAM)

-- 13) Criação de 1 TRIGGER e 1 STORED PROCEDURE

CREATE TABLE AuditoriaJogador (
	id_auditoria INTEGER AUTO_INCREMENT PRIMARY KEY,
	id_jogador INTEGER,
	nome VARCHAR(100),
	data_inativacao DATETIME
); -- (ARMAZENAR A AUDITORIA DE JOGADORES INATIVADOS)

DELIMITER $$

CREATE TRIGGER trg_InativarJogador
AFTER UPDATE ON Jogador
FOR EACH ROW
BEGIN
IF NEW.status = 'I' AND OLD.status != 'I' THEN
INSERT INTO AuditoriaJogador (id_jogador, nome, data_inativacao)
VALUES (NEW.id_jogador, NEW.nome, NOW());
END IF;
END $$

DELIMITER ; -- (TODA VEZ QUE O STATUS DE UM JOGADOR FOR ALTERADO PARA 'I' (INATIVO), A TRIGGER REGISTRA O ID, NOME E DATA DE INATIVAÇÃO NA TABELA AuditoriaJogador.)

DELIMITER $$

CREATE PROCEDURE TotalBonificacaoPorEquipe (
IN equipe_id INT
)
BEGIN
SELECT e.nome AS equipe,
SUM(t.bonificacao) AS total_bonificacao
FROM Equipe e
JOIN Torneio t ON t.fk_Equipe_id_equipe = e.id_equipe
WHERE e.id_equipe = equipe_id
GROUP BY e.nome;
END $$

DELIMITER ;

CALL TotalBonificacaoPorEquipe(1); -- (EXIBIR O TOTAL DE BONIFICAÇOES RECEBIDAS POR UMA EQUIPE ESPECÍFICA)
