# Game-S-Core

Este é um projeto do meu trabalho de Página Web 2 (PW2) junto com um colega de classe LOrnellas131, <br>
o trabalho consiste em criar uma uma página web que possua acesso a um banco de dos e consiga <br>
realizar um CRUD (Create Read Update Delete), e o nossa idéia foi criar um E-Commerce de jogos, <br>
o CRUD está presente na compra, visualização, alterar o saldo e excluir os jogos, além de outras coisas, <br>
nome do nosso site é Game S Core, uma piada, onde dependo da interpretação do usuário, pode ser "Games Core" <br>
algo como Núcleo de jogos, ou "Game Score" que seria Pontuação de jogos, o site possui uma interface simples, <br>
porém funcional.

<h1>Banco de Dados</h1>

create database gamescorebd;
use gamescorebd;

create table users(
	id int auto_increment primary key,
    name varchar(1055),
    email varchar(345) UNIQUE,
    senha varchar(255),
    saldo decimal(8, 2)
);

create table games(
	id int auto_increment primary key,
	name varchar(100),
    price decimal(5, 2),
    autor varchar(255),
    autorid int(6),
    description varchar(100),
    img varchar(104)
);

INSERT INTO games (name, price, autor, autorid, description, img) VALUES
("Grounded", 100.00, "Nintendo", 1964, "Sobreviva no quintal encolhido ao tamanho de um inseto.", "grounded.png"),
("Guilty Sock", 64.50, "SEGA", 1999, "Meias brigando em tribunais surreais", "guiltySock.png"),
("Hollow Knight", 34.00, "HAL. Laboratory", 10, "Explore um reino sombrio em combate metroidvania.", "hollowKnight.png"),
("inscryption", 69.99, "Nintendo", 1005, "Terror psicológico com cartas e quebra-cabeças.", "inscryption.png"),
("Minecraft", 130.00, "Toby Fox", 34, "Crie e sobreviva em mundos infinitos.", "minecraft.png"),
("Papers Please", 99.99, "Nintendo", 1005, "Inspecione documentos e decida destinos.", "papersPlease.png"),
("Peak", 30.00, "Ubisoft", 100, "Escale montanhas e sobreviva à natureza.", "peak.png"),
("Treasure", 199.99, "Square", 30, "Caça ao tesouro em aventuras fantásticas.", "treasure.png");

create table users_games(
	id_user int,
    id_game int,
    primary key (id_user, id_game),
    foreign key(id_user) references users(id) on delete cascade,
    foreign key(id_game) references games(id) on delete cascade
);

select * from users;
select * from games;
select * from users_games;

drop table users; -- drop destroi a TABELA
truncate table users; -- truncate destroi os DADOS da tabela
drop table games;
truncate table games;
drop table users_games;
truncate table users_games;

start transaction;
rollback; -- Voltar
commit; -- Avançar
