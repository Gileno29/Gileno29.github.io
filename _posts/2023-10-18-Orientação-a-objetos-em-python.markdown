---
layout: post
title:  "Orientação a Objetos em Python"
date:   2023-10-18 13:37
categories: IT Programing
---
<p style="text-align:justify;"> O python assim como outras linguagens implementa o paradigma de orientação a objetos durante esse mini tutorial vamos ver alguns exemplos de como isso é feito nessa linguagem.</p>

### Orientação a objetos

<p style="text-align: justify;"> Antes de falarmos diretamente sobre o assunto é importante relembrar de alguns conceitos essenciais de orientação a o objetos, vamos lá.</p>

#### abstração 
<p style="text-align: justify"> A abstração e um dos pontos mais cruciais dentro de linguagens que implementam Orientação a Objetos, como estamos lidando com uma representação de um objeto real, é preciso imaginar o que esse objeto irá realizar dentro de nosso sistema.</p>

#### Identidade
<p style="text-align: justify"> É preciso dar uma identidade ao objetos que criamos essa identidade deve ser unica dentro do sistema para evitar conflitos, devido a isso várias liguagens implementam o conceito de pacotes ou namespaces evitando assim que o objetos se repita dentro do pacote. </p>

#### Caracteristicas
<p style="text-align: justify"> No mundo real qualquer objeto possui elementos que o definem, em orientação a objetos esses elementos são nomeados de propriedades ou atributos, por exemplo, um carro poderia ter como propriedades cor, modelo, placa e valor. </p>



#### Ações dos objetos
<p style="text-align: justify"> Por fim é preciso definir as ações do objeto em questão essas ações dentro do mundo de orientação a objetos são chamados de de métodos, tomando como exemplo o objeto corro ele poderia implementar os metodos Ligar() Acelerar() Frear() e Desligar(), esses metodos vão possuir definido em seu interior todo o código para que eles funcionem de forma efetiva.</p>

<p style="text-align: justify;"> bem tendo relembrado isso podemos processeguir. Caso queiram mais detalhes podem ler esse <a href="https://www.devmedia.com.br/os-4-pilares-da-programacao-orientada-a-objetos/9264">artigo</a> da devimedia.com.br que foi de onde resumi grande parte das informações a respeito dos conceitos</p>

#### Declarando classes
<p style="text-align:justify"> Dentro do paradigma de orientação a objetos é a representação, uma abstração do mundo real, para declararmos uma classe em python</p>

```py 
    class ContaBancaria():
        # Atributos e métodos da sua classe
        self.agencia='0'
        self.conta=''
        self.saldo=0.00
        self.ativo=True

```

<p style="text-align:justify"> quando buscamos iniciar obrigatoriamente nossos objetos com valores podemos utilizar de contrutores, dentro do python pode ser feito da seguinte forma:</p>

```py
class ContaBancaria:
    def __init__(self, agencia, conta, saldo):
        self.agencia = agencia
        self.conta = conta
        self.saldo = saldo
        self.ativo=True

```
<p style="text-align: justify;">Para instanciarmos objetos com python podemos fazert da seguinte maneira:</p>



```py 
class ContaBancaria:
    def __init__(self, agencia, conta, saldo):
        self.agencia = agencia
        self.conta = conta
        self.saldo = saldo
        self.ativo=True



if __name__ == "__main__":
    cb1 = ContaBancaria("0001", "2232", "0")
    print(cb1.conta)

```
<p style="text-align: justify;"> Ao se executar o código acima vamos criar um obejto do tipo conta bancaria, e iniciarmos ele com uma agencia, conta e um saldo   </p>
<p style="text-align: justify;">Como sabemos uma classe possui atributos (que definem suas características) e métodos (que definem seus comportamentos). Vamos criar agora um metodo para a classe conta bancaria.</p>


```py 
class ContaBancaria:
    def __init__(self, agencia, conta, saldo):
        self.agencia = agencia
        self.conta = conta
        self.saldo = saldo
        self.ativo=True

    def desativar(self):
        self.ativo=False
        print("Conta bancaria desativada com sucesso")



if __name__ == "__main__":
    cb1 = ContaBancaria("0001", "2232", "0")
    print(cb1.conta)

```

<p style="text-align: justify;">Agora vamos entrar em um conceito importandte dentro desse universo: Atributos de visibilidade.</p>
<p style="text-align: justify;">Bem, para iniciarmos existem 3 tipos de atributos de visibilidade,Public, Private e Protect.</p>
  - Public: Atrivbutos e métodos públicos podem ser acessados e modificados de qualquer parte do projeto.
  - Private: Atributos e métodos definidos como privados só poderão ser  invocados, acessados ou modificados somente por seu proprio projeto(modulo). 
  - Protected: Atributos e métodos protegidos só podem ser invocados, acessados e modificados  por classes que herdam de outras classes através do conceito de herança.

<p style="text-align: justify;">O Python ao contrario de outras linguagens como o Java que é voltada  por completo ao paradigma de orientação a objetos implementa esses atributos só que a sua própria maneira</p>
<p style="text-align: justify;">Caso desejamos torna os privados os atributos dessa classe poderiamos por "__"  no inicio de seus nomes.</p>

```py
class ContaBancaria:
    def __init__(self, agencia, conta, saldo):
        self.__agencia = agencia
        self.__conta = conta
        self.__saldo = saldo
        self.__ativo=True

    def desativar(self):
        self.__ativo=False
        print("Conta bancaria desativada com sucesso")



if __name__ == "__main__":
    cb1 = ContaBancaria("0001", "2232", "0")
    print(cb1.conta)
```
<p style="text-align: justify;">porém no python isso não passa de uma convenção, significa que é uma ideologia criada pelos desenvolvedores, poŕem esses atributos continuariam acessiveis de fora da classe</p>