# Game-S-Core

<h2>Sobre o projeto</h2>
	Este é um projeto do meu trabalho de Página Web 2 (PW2) junto com um colega de classe LOrnellas131, <br>
o trabalho consiste em criar uma uma página web que possua acesso a um banco de dos e consiga <br>
realizar um CRUD (Create Read Update Delete), e o nossa idéia foi criar um E-Commerce de jogos, <br>
o CRUD está presente na compra, visualização, alterar o saldo e excluir os jogos, além de outras coisas, <br>
nome do nosso site é Game S Core, uma piada, onde dependo da interpretação do usuário, pode ser "Games Core" <br>
algo como Núcleo de jogos, ou "Game Score" que seria Pontuação de jogos, o site possui uma interface simples, <br>
porém funcional.

<h2>Banco de Dados</h2>
<br>
Abaixo está o código do banco de dados que nós utilizamos:
<br>
create database gamescorebd;<br>
use gamescorebd;<br>
<br>
create table users(<br>
    id int auto_increment primary key,<br>
    name varchar(1055),<br>
    email varchar(345) UNIQUE,<br>
    senha varchar(255),<br>
    saldo decimal(8, 2)<br>
);<br>
<br>
create table games(<br>
	id int auto_increment primary key,<br>
	name varchar(100),<br>
    price decimal(5, 2),<br>
    autor varchar(255),<br>
    autorid int(6),<br>
    description varchar(100),<br>
    img varchar(104)<br>
);<br>
<br>
INSERT INTO games (name, price, autor, autorid, description, img) VALUES<br>
("Grounded", 100.00, "Nintendo", 1964, "Sobreviva no quintal encolhido ao tamanho de um inseto.", "grounded.png"),<br>
("Guilty Sock", 64.50, "SEGA", 1999, "Meias brigando em tribunais surreais", "guiltySock.png"),<br>
("Hollow Knight", 34.00, "HAL. Laboratory", 10, "Explore um reino sombrio em combate metroidvania.", "hollowKnight.png"),<br>
("inscryption", 69.99, "Nintendo", 1005, "Terror psicológico com cartas e quebra-cabeças.", "inscryption.png"),<br>
("Minecraft", 130.00, "Toby Fox", 34, "Crie e sobreviva em mundos infinitos.", "minecraft.png"),<br>
("Papers Please", 99.99, "Nintendo", 1005, "Inspecione documentos e decida destinos.", "papersPlease.png"),<br>
("Peak", 30.00, "Ubisoft", 100, "Escale montanhas e sobreviva à natureza.", "peak.png"),<br>
("Treasure", 199.99, "Square", 30, "Caça ao tesouro em aventuras fantásticas.", "treasure.png");<br>
<br>
create table users_games(<br>
    id_user int,<br>
    id_game int,<br>
    primary key (id_user, id_game),<br>
    foreign key(id_user) references users(id) on delete cascade,<br>
    foreign key(id_game) references games(id) on delete cascade<br>
);<br>
<br>
select * from users;<br>
select * from games;<br>
select * from users_games;<br>
<br>
drop table users; -- drop destroi a TABELA<br>
truncate table users; -- truncate destroi os DADOS da tabela<br>
drop table games;<br>
truncate table games;<br>
drop table users_games;<br>
truncate table users_games;<br>
<br>
start transaction;<br>
rollback; -- Voltar<br>
commit; -- Avançar<br>
