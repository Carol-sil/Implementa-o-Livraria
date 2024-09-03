create database Livraria;
use Livraria;

create table Cliente (
idCliente int not null,
nome varchar(50) not null,
telefone varchar(20) not null,
email varchar(50) not null,
endereco varchar(100) not null,
primary key (idCliente)
);

create table Editora (
idEditora int not null,
nome varchar(50) not null,
telefone varchar(20) not null,
email varchar(50) not null,
endereco varchar(100) not null,
primary key (idEditora)
);

create table Livro (
idLivro int not null,
idEditora int not null,
titulo varchar(100) not null,
autor varchar(50) not null,
ano int not null,
ISBN varchar(20),
preco decimal (5,2),
primary key (idLivro),
foreign key (idEditora) references Editora(idEditora)
);

create table Pedido (
idPedido int not null,
idCliente int not null,
dataPedido date not null,
valorPedido decimal(5,2) not null,
primary key (idPedido),
foreign key (idCliente) references Cliente (idCliente)
);

create table itemPedido (
idPedido int not null,
idLivro int not null,
quantidade int not null,
valoritemPedido decimal(5,2) not null,
foreign key (idPedido) references Pedido (idPedido),
foreign key (idLivro) references Livro (idLivro)
);

create table Estoque (
idLivro int not null,
quantidade int not null,
foreign key (idLivro) references Livro (idLivro)
);

insert into Cliente (idCliente, nome, telefone, email, endereco) values
     (1, 'Alice de Souza', '(41) 99854-5648', 'alice.s@email.com.br', 'Rua das Flores, 3578, Curitiba - PR'),
     (2, 'Mario Vicente', '(11) 99527-3721', 'mario.v@email.com.br', 'Avenida Ipiranga, 1246, apto. 201, São Paulo - SP'),
     (3, 'Maria Helena Mantovani', '(21) 99763-1213', 'maria.m@email.com.br', 'Rua Vicente Machado, 10503, apto. 1007, Rio de Janeiro - RJ'),
     (4, 'Vitor Martins', '(85) 98754-2050', 'vitor.m@email.com.br', 'Rua Osvaldo Cruz, 578, Fortaleza - CE'),
     (5, 'Nicole Amanda de Jesus', '(92) 98418-3141', 'amanda.j@email.com.br', 'Rua Venezuela, 649, Manaus - AM'),
     (6, 'Luciano Tucolo', '(51) 99234-5458', 'luciano.t@email.com.br', 'Avenida Uruguai, 3152, apto. 2202, Porto Alegre - RS'),
     (7, 'Paula Roberta Vitorino', '(65) 98953-7828', 'paula.v@email.com.br', 'Rua dos Açudes, 1029, Cuiabá - MT'),
     (8, 'Guilherme Koeriche', '(63) 99315-6264', 'guilherme.k@email.com.br', 'Avenida Brasil, 953, apto. 709, Palmas - TO'),
     (9, 'Beatriz Leopoldina', '(71) 99264-3585', 'beatriz.l@email.com.br', 'Rua dos Baianos, 12549, Salvador - BA'),
     (10, 'Lucas Cochuelo', '(69) 98767-1545', 'lucas.c@email.com.br', 'Rua Indenpendente, 209, Porto Velho - RO');

insert into Editora (idEditora, nome, telefone, email, endereco) values
     (1, 'Companhia da Leitura', '(11) 3854-2946', 'companhiadaleitura@email.com.br', 'Avenida Brasil, 458, São Paulo - SP'),
     (2, 'Arco da Velha', '(21) 3916-5859', 'arcodavelha@email.com.br', 'Rua das Estradas de Pedras, 568, sala 12, Rio de Janeiro - RJ'),
     (3, 'Mais Informática', '(62) 3425-2064', 'maisinformatica@email.com.br', 'Avenida Linda de Goiás, 627, Goiânia - GO'),
     (4, 'Sexta dos Estudos', '(41) 3789-3438', 'sextadosestudos@email.com.br', 'Rua Sete de Setembro, 1568, sala 29, Curitiba - PR'),
     (5, 'Ciência da Informação', '(11) 3678-1284', 'cienciadainformacao@email.com.br', 'Rua Vinte e Cinco de Maio, 678, sala 3, São Paulo - SP');

insert into Livro (idLivro, idEditora, titulo, autor, ano, ISBN, preco) values
     (1, 1, 'Minha Faculdade Vai Me Enlouquecer', 'Murilo dos Santos', 2023, '978-0-1548-6458-4', 29.90),
     (2, 1, 'Controlando as Emoções', 'Letícia de Munhoz Neta', 2021, '123-0-2054-4896-7', 35.90),
     (3, 1, 'Brasil Brasileiro', 'Mariana Luiza de Andrade', 2020, '578-0-4586-2946-2', 49.90),
     (4, 2, 'Se Eu Voltasse no Passado', 'Dionísio Siqueira', 2021, '248-0-1029-3045-4', 42.90),
     (5, 2, 'Penso, Logo Existo', 'Ana Martinha Ramos', 2019, '745-0-3486-5149-6', 55.90),
     (6, 2, 'Lugares para Viajar Sozinho', 'Maurício de Andrade', 2022, '647-0-6128-9745-1', 69.90),
     (7, 3, 'Aprendendo Python em 24 Horas', 'Joaquim Luiz Machado', 2019, '358-0-7458-6485-5', 99.90),
     (8, 3, 'Banco de Dados: Aprenda de Forma Simples e Fácil', 'Pedro Antônio Zamba', 2018, '942-0-8125-6479-8', 119.90),
     (9, 3, 'Java para Que Te Quero', 'Luíza Soraia do Nascimento', 2019, '834-0-4726-1495-9', 99.90),
     (10, 4, 'Matemática Descomplicada', 'Ana Luíza de Souza', 2017, '356-0-2746-9175-2', 79.90),
     (11, 4, 'Português para Estrangeiros', 'Vinícius Matheus Furlan', 2018, '674-0-4861-3186-3', 89.90),
     (12, 4, 'Estatística é para Todos', 'Sofia Castela', 2020, '527-0-2943-4715-5', 59.90),
     (13, 5, 'Big Data: Conhecimentos Essenciais', 'Ana Daniela Vivan', 2023, '453-0-2495-8371-8', 121.90),
     (14, 5, 'Ciência de Dados: O Futuro', 'João Paulo Macedo', 2024, '924-0-7165-6249-9', 149.90),
     (15, 5, 'Inteligência Artificial Aplicada a Dados', 'Marli Terezinha Girotto', 2023, '694-0-1973-4826-7', 169.90);

insert into Estoque (idLivro, quantidade) values
     (1, 35),
     (2, 20),
     (3, 50),
     (4, 50),
     (5, 40),
     (6, 70),
     (7, 150),
     (8, 125),
     (9, 140),
     (10, 100),
     (11, 75),
     (12, 50),
     (13, 150),
     (14, 170),
     (15, 135);

insert into Pedido (idPedido, idCliente, dataPedido, valorPedido) values
     (1, 1, '2021-09-09', 42.90),
     (2, 2, '2021-10-29', 119.90),
     (3, 3, '2022-02-18', 147.70),
     (4, 4, '2022-03-08', 89.90),
     (5, 5, '2022-11-15', 99.90),
     (6, 6, '2023-01-04', 59.80),
     (7, 7, '2023-05-09', 119.80),
     (8, 8, '2023-07-26', 169.90),
     (9, 9, '2023-08-19', 59.90),
     (10, 10, '2023-10-03', 271.80),
     (11, 3, '2023-11-28', 42.90),
     (12, 6, '2023-12-07', 201.80),
     (13, 9, '2024-01-03', 99.90);

insert into ItemPedido (idPedido, idLivro, quantidade, valorItemPedido) values
     (1, 4, 1, 42.90),
     (2, 8, 1, 119.90),
     (3, 5, 2, 111.80),
     (3, 2, 1, 35.90),
     (4, 11, 1, 89.90),
     (5, 9, 1, 99.90),
     (6, 1, 2, 59.80),
     (7, 6, 1, 69.90),
     (7, 3, 1, 49.90),
     (8, 15, 1, 169.90),
     (9, 12, 1, 59.90),
     (10, 14, 1, 149.90),
     (10, 13, 1, 121.90),
     (11, 4, 1, 42.90),
     (12, 10, 1, 79.90),
     (12, 13, 1, 121.90),
     (13, 7, 1, 99.90);

select (nome) as 'Nomes'
from Cliente order by nome;

select Editora.nome as 'Editora', Livro.titulo as 'Livro'
From Editora
inner join Livro on Editora.idEditora = Livro.idEditora
order by Editora desc;

select Editora.nome as 'Editora', round(avg (Livro.preco), 2) as 'preco médio'
From Editora
inner join Livro on Editora.idEditora = Livro.idEditora
Group by Editora;

select Cliente.nome as 'Cliente', SUM(itemPedido.quantidade) as 'Livros Comprados'
From Cliente
inner join Pedido on Pedido.idCliente = Cliente.idCliente
inner join itemPedido on Pedido.idPedido = itemPedido.idPedido
group by Cliente.nome;
