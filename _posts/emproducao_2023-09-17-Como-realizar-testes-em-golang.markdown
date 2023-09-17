---
layout: post
title:  "Criando Testes para APIs em golang"
date:   2023-09-17 08:37
categories: IT
---
<p style="text-align:justify;"> O postgres é um dos bancos de dados relacionais mais utilizados recentemente, devido a sua conformidade com ACID(Atomicidade, consistencia isolamento e duarabilidade) em todas as suas configurações além de implementar diferentes algoritimos para controle de índice como arvores e índices de expressão que até então não são implementados em alguns outros bancos relacionais como o MySQL, existem inúmeros artigos na internet falando sobre diferenças entre esses bancos e realizando comparativos entre eles, o ponto aqui não é esse, mas aos interesados vou deixar o link de um artigo da AWS sobre o tema nesse <a href="https://aws.amazon.com/pt/compare/the-difference-between-mysql-vs-postgresql/">link</a>. Nesse post vou repassar uma situação simples porém para iniciantes pode ser um pouco complicado de realizar, vou apresentar como é possível instalar o postgres no linux, mais precisamente no ubuntu 22.04 lts e algumas configurações básicas que podem ser realizadas.Bem vamos lá!.</p>