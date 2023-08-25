---
layout: post
title:  "Instalando o PostgreSQL no Ubuntu 22.04 lts"
date:   2023-08-21 08:37
categories: IT
---
<p style="text-align:justify;"> O postgres é um dos bancos de dados relacionais mais utilizados recentemente, devido a sua conformidade com ACID(Atomicidade, consistencia isolamento e duarabilidade) em todas as suas configurações além de implementar diferentes algoritimos para controle de índice como aravores e indices de expressão que até então não são implementados em outros bancos relacionais como o MySQL, existem inúmeros artigos na internet falando sobre diferenças entre esses bancos e realizando comparativos entre eles, o ponto aqui não é esse, mas aos interesados vou deixar o link de um artigo da AWS sobre o tema nesse <a href="https://aws.amazon.com/pt/compare/the-difference-between-mysql-vs-postgresql/">link</a>. Nesse post vou repassar uma situação simples porém para iniciantes pode ser um pouco complicado de realizar, vou apresentar como é possível instalar o postgres no linux, mais precisamente no ubuntu 22.04 lts e algumas configurações básicas que podem ser realizadas.Bem vamos lá!.</p>

## Instalação
- Atualize seus repositorios.
```bash
	apt-get update
 ```

- Instale o postgres com o seguinte linha de comando:
```bash
	sudo apt install postgresql postgresql-contrib
```

<p style="text-align:justify;">A opção -contrib permite que seja utilizado alguns modulos adicionais caso seja preciso para algo, não é obrigatorio instalar, então pode ser deixado de lado no momento da instlação se você não precisa de algum desses modulos específicos. <a href="https://www.mankier.com/package/postgresql-contrib">Aqui</a> tem uma lista desses modulos do pacote.</p>

<p style="text-align:justify;">após a instalação finalizar o postgres por padrão vai ccriar um usuario em sua máquina chamdo postgres e você pode utilizar esse usuario para logar no banco de dados. Como isso funciona? Bem o postgres trabalha com esquema de "ROLES" para gerenciamento de usuarios e permicionamento, no final é bem similar ao users e groups de sistemas Linux/Unix, após está instalado o postgres vai utilizar ident authentication traduzindo: Ele vai associar usuarios de seu sistema como alguma ROLE que Esteja configurada nele, nesse caso a ROLE postgres que vai ser associada ao usuario postgres.</p>

## Acesso e configuração
Vamos agora logar no baco de dados.
Para logar no banco de dados existe algumas formas, vou passar a que acredito ser mais simpres e intuitiva:

- <p style="text-align:justify;">Acesse o usuario postgres a partir do seu usuario root</p>
```bash
   $ su postgres
```
- <p style="text-align:justify;">Acesse o banco de dados com comando psql </p>
```bash
   $ psql
```
 - <p style="text-align:justify;">Você vai cair na tela de acesso do postgreSQL. </p>
```bash
	psql (14.9 (Ubuntu 14.9-0ubuntu0.22.04.1))
	Type "help" for help.

	postgres=#
```


<p style="text-align:justify;">Pronto a partir desse momento já pode ser criado databases novas roles para Gerenciamento das informações e o que mais seja necessário. Porém vamos dizer que você deseja por um pouco mais de segurança no acesso a seu database, que você deseja que mesmo quem esteja logado como root em seu servidor não consiga acessar diretamente seu banco de dados com um simples "psql" para isso vamos precisar configurar uma senha para nosso usuario postgres.</p>

- <p style="text-align:justify;">Para configurar uma senha para o usuario postgres podemos fazer da seguinte forma:</p>
```bash
	postgres=# \password
	Enter new password for user "postgres":
```

<p style="text-align:justify;"> O banco vai pedir para confirmar a senha após isso, se elas não forem iguasi a operação não vai funcionar. Após isso vai ser preciso acessar o arquivo de configuração do postgres que fica no seguinte path:/etc/postgresql/sua_versao_do_postgres/main/pg_hba.conf.
O arquivo vai possuir uma linha com a seguinte designação:</p>

```bash
# DO NOT DISABLE!
# If you change this first entry you will need to make sure that the
# database superuser can access the database using some other method.
# Noninteractive access to all databases is required during automatic
# maintenance (custom daily cronjobs, replication, and similar tasks).
#
# Database administrative login by Unix domain socket
local   all         	postgres                            	peer

# TYPE  DATABASE    	USER        	ADDRESS             	METHOD

# "local" is for Unix domain socket connections only
```
 - <p style="text-align:justify;">Altere o peer para md5 e restart o servico do banco de dados:</p>
```bash
	sudo service postgresql restart
 ```
 ```bash
	$root: /home/gileno ❯ psql -U postgres
	Password for user postgres:
 ```
<p style="text-align:justify;">Pronto, com isso você configurou uma senha em seu usuário postgres. </p>