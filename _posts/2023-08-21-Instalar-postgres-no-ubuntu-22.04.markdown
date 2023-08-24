O postgres é um dos bancos de dados relacionais mais utilizados recentemente, devido a sua conformidade com ACID(Atomicidade, consistencia isolamento e duarabilidade) em todas as suas configurações além de implementar diferentes algoritimos para controle de índice como aravores e indices de expressão que até então não são implementados em outros bancos relacionais como o MySQL, existem inúmeros artigos na internet falando sobre diferenças entre esses bancos e realizando comparativos entre eles, o ponto aqui não é esse, mas aos interesados vou deixar o link de um artigo da AWS sobre o tema nesse [link](https://aws.amazon.com/pt/compare/the-difference-between-mysql-vs-postgresql/). Nesse post vou repassar uma situação simples porém para iniciantes pode ser um pouco complicado de realizar, vou apresentar como é possível instalar o postgres no linux, mais precisamente no ubuntu 22.04 lts e algumas configurações básicas que podem ser realizadas.
Bem vamos lá!.

# Instalação
- Atualize seus repositorios.
```bash
    apt-get update
 ```

- Instale o postgres com o seguinte linha de comando:
```bash
    sudo apt install postgresql postgresql-contrib
```

A opção -contrib permite que seja utilizado alguns modulos adicionais caso seja preciso para algo, não é obrigatorio instalar, então pode ser deixado de lado no momento da instlação se você não precisa de algum desses modulos específicos. [Aqui](https://www.mankier.com/package/postgresql-contrib) tem uma lista desses modulos do pacote.

após a instalação finalizar o postgres por padrão vai ccriar um usuario em sua máquina chamdo postgres e você pode utilizar esse usuario para logar no banco de dados. Como isso funciona? Bem o postgres trabalha com esquema de "ROLES" para gerenciamento de usuarios e permicionamento, no final é bem similar ao users e groups de sistemas Linux/Unix, após está instalado o postgres vai utilizar ident authentication traduzindo: Ele vai associar usuarios de seu sistema como alguma ROLE que Esteja configurada nele, nesse caso a ROLE postgres que vai ser associada ao usuario postgres.

# Acesso e configuração
Vamos agora logar no baco de dados.
Para logar no banco de dados existe algumas formas, vou passar a que acredito ser mais simpres e intuitiva:

- Acesse o usuario postgres a partir do seu usuario root
```bash
   $ su postgres
```
- Acesse o banco de dados com comando psql
```bash
   $ psql
```
 - Você vai cair na tela de acesso do postgreSQL.
```bash
    psql (14.9 (Ubuntu 14.9-0ubuntu0.22.04.1))
    Type "help" for help.

    postgres=#
```

Pronto a partir desse momento já pode ser criado databases e novos “ROLES” para gerenciamento do banco de dados. Porém vamos dizer que você deseja pôr um pouco mais de segurança no acesso a seu database, que você deseja que mesmo quem esteja logado como root em seu servidor não consiga acessar diretamente seu banco de dados com um simples "psql" para isso vamos precisar configurar uma senha para nosso usuário postgres.
