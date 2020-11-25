# ReactAnime# AnimeHub 

#### Introdução 


Nosso site consiste no entreterimento de nossos clientes. 
Com animes de alta qualidade, e com dublagem absoluta.

Procuramos o entretenimento , com animes para crianças adultos e
adolescentes.<br>
 Nosso projeto consiste na pessoa assistir animes e comprar
mangas em formato pdf.


## Casos de Uso
![](https://i.imgur.com/VA8XEiM.png)




### Usuário
O Usuário pode acessar o site, criar cadastros e fazer login (Diferente do Gerente ele precisa fazer cadastro). Podendo consultar os animes e assisti-los, pode comprar os Mangás da nossa loja AnimeHub. 
Assim podendo pagar com todas as formas disponíveis do site, sejam elas: Paypal, Pagseguro, Boleto, Cartão.

## Mer
![](https://i.imgur.com/gV9Aoc4.png)

###create database sitebd;

use sitebd;

show tables;

create table tb_anime (
id_anime int primary key auto_increment,
nm_anime varchar(100),
vl_duracao decimal(15,5),
nr_classificacao_idade int,
dt_lancamento date,
vl_avaliacao decimal(15,5),
nm_autor varchar(100),
ds_genero varchar(100),
img_capa varchar(100)
);

create table tb_permissao (

id_permissao int primary key auto_increment,
id_funcionario int,
id_anime int,
id_manga int,
bt_alterar_anime bool,
bt_add_anime bool,
bt_alterar_manga bool,
bt_visualizar bool,
Foreign key (id_funcionario) references tb_funcionario (id_funcionario),
Foreign key (id_anime) references tb_anime (id_anime),
Foreign key (id_manga) references tb_manga (id_manga)
);

create table tb_manga (
id_manga  int primary key auto_increment,
nm_manga varchar(100),
vl_preco decimal(15,5),
dt_lancamento date,
nm_autor varchar(100),
ds_genero varchar(100),
nr_classificacao_idade int,
vl_avaliacao decimal(15,5),
qt_pagina int,
bt_disponivel bool,
img_capa varchar(100)
);

create table tb_funcionario(
id_funcionario  int primary key auto_increment,
nm_funcionario varchar(100),
dt_nascimento date,
nr_rg int,
nr_cpf int,
nr_telefone int,
ds_endereco varchar(100),
ds_email varchar(100),
dt_ultimo_acesso date
);

create table tb_cliente (

id_cliente  int primary key auto_increment,
id_login int,
nm_cliente varchar(100),
nr_cpf int,
nr_telefone int,
dt_ultimo_acesso date,
dt_nascimento date,
Foreign key (id_login) references tb_login (id_login)
);

create table tb_login (
id_login int primary key auto_increment,
ds_email varchar(100),
ds_senha varchar(100)
);

create table tb_compra (

id_compra int primary key auto_increment,
id_cliente int,
bt_pago bool,
bt_cartao bool,
bt_pay_pal bool,
bt_pague_seguro bool,
dt_dia_compra date,
Foreign key (id_cliente) references tb_cliente (id_cliente)
);

create table tb_compra_manga (

id_compra_manga int primary key auto_increment,
id_compra int,
id_manga int,
vl_total decimal(15,5),
qt_manga int,
Foreign key (id_compra) references tb_compra (id_compra),
Foreign key (id_manga) references tb_manga (id_manga)
);

create table tb_manga (
id_manga int primary key auto_increment,
nm_manga varchar(100),
vl_preco decimal(15,5),
nm_autor varchar(100),
ds_genero  varchar(100),
nr_classificacao_idade int,
vl_avaliacao decimal(15,5),
qt_pagina int,
bt_disponivel bool,
img_capa_manga varchar(100)
);


## Prototipação 

#### Primeira tela 
Tela de Principal Todas as pessoas que clicam no link do site é direcionada à esta tela onde se encontra a logo do nosso site, o Botão de fazer login, um botão de compra e um rodapé.
![](https://i.imgur.com/pGTlTVp.png)
****

#### Tela de Login
onde conseguimos fazer login e entrar no site, ele precisa das credenciais do cadastro. Nele contém o criar conta se o cliente não tiver feito uma conta ainda. E contendo esqueceu a senha, onde o cliente pode 

![](https://i.imgur.com/vBNeS9b.png)
****

#### Criar conta 
Onde o cliente pode fazer sua conta. 
Para fazer sua conta precisamos de 4 credenciais. 
CPF – Onde o cliente só pode acessar o site com o CPF 
Telefone – Onde o cliente é obrigado a colocar o telefone.
E-MAIL – Onde o cliente terá que colocar o E-mail para se cadastrar 
SENHA – Onde o cliente precisará colocar sua senha, para criar sua conta. 
Depois de todos os tópicos apresentados, o cliente poderá acessar o site.
![](https://i.imgur.com/KwxM18p.png)
****

#### Acessar 
Nossa tela de assistir contém todos os animes disponíveis no momento. 
Contém um carrossel, onde o usuário ver, para acessar os melhores animes no momento. 
E temos 6 cards, onde ficam os animes disponíveis para assistir.
Clicando em cada um deles, você é direcionado a página do anime escolhido pelo usuário.
![](https://i.imgur.com/XmZxH3H.png)
****
#### Assistir
Quando o usuário escolhe o anime que deseja assistir, ele é direcionado para esta tela. 
Onde podemos assistir o anime escolhido, contendo as informações do anime. 
Clicando na parte superior, com um ícone de carrinho podemos ser direcionados a parte de comprar de Mangás. 
 

![](https://i.imgur.com/wxzrINX.png)
****
#### Comprar
Tela de compras, podemos acessar os Mangás para a compra.
Onde se encontra diversos Mangás, com diversos preços. Temos os Mangás mais novos e lançamentos, e temos os mais antigos e mais famosos.
Todos eles são adquiridos virtualmente, ou seja, podemos comprar dentro do site mesmo. 
![](https://i.imgur.com/OdTNFSU.png)
****

#### Produto
Quando escolhermos o Mangá que queremos adquirir, somos direcionados à esta tela. Onde se encontra o processo do produto, a quantidade do produto.
E temos o botão comprar onde somos direcionados a outra pagina, que seria o Pagamento. 
![](https://i.imgur.com/YcIl5kh.png)
***

#### Finalizar pedido
Para finalizar o pedido, podemos escolher diversas formas de fazer o pagamento. 
Seja boleto 
Ou em cartão 
Até mesmo em Paypal (Um dos aplicativos de banco online mais confiáveis do mundo)
E não esquecendo a PagSeguro.
![](https://i.imgur.com/tYlEWsR.png)
Finalizar pedido
Para finalizar o pedido, podemos escolher diversas formas de fazer o pagamento. 
Seja boleto 
Ou em cartão 
Até mesmo em Paypal (Um dos aplicativos de banco online mais confiáveis do mundo)
E não esquecendo a PagSeguro.


## Integrantes da StacksTech

#### Lucas Francisco N°23
#### Djalma Prado    N°09
#### Pedro Staaks    N°34
#### Davi luiz       N°08
#### Nicolas Torres  N°
#### Guilherme       N°
*******

## Links 
https://trello.com/b/FCPmcP93/tcc









