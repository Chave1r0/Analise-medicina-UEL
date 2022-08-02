# Analise-medicina-UEL
Utilizei o SQL para responder perguntas sobre os classificados e convocados em algumas medicinas na universidade estadual de Londrina nos últimos 3 anos;
Este foi meu primeiro "projeto" para tratamento de dados com SQL; Retirei estes dados do site da COPS UEL.
O código segue logo abaixo:

      SELECT COUNT(nome) AS "N° de classificados"
    FROM meduel.dbo.classificados
    -- nos ultimos 3 anos, 1330 vestibulandos foram classificados para o curso de medicina da UEL

    SELECT COUNT(nome) AS "N° de convocados"
    FROM meduel.dbo.convocados
    -- nos últimos 3 anos, 286 vestibulandos foram convocados para o curso de medicina da UEL

    SELECT COUNT(class.nome) AS "N° de não convocados"
    FROM meduel.dbo.classificados AS class
    LEFT JOIN meduel.dbo.convocados AS con ON class.nome = con.nome
    WHERE con.nome IS NULL
    -- nos últimos 3 anos, 981 dos classificados em medicina na UEL não foram convovados.

    SELECT nome as "Nome"
    FROM meduel.dbo.classificados
    GROUP BY nome
    HAVING COUNT(nome) = 3
    -- nos últimos 3 anos, 18 vestibulandos ficaram na lista de convocação dos anos de 20/21/22

    SELECT class.nome as "Nome"
    FROM meduel.dbo.classificados AS class
    INNER JOIN meduel.dbo.convocados AS con ON class.nome = con.nome
    GROUP BY class.nome
    HAVING COUNT(class.nome) = 3
    -- Dos 18 vestibulandos que ficaram na lista de classificação dos anos de 20/21/22, 7 deles foram aprovados em 2022
