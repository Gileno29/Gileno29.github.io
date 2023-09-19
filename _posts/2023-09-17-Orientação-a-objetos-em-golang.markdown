---
layout: post
title:  "Orientação a Objetos em golang"
date:   2023-09-17 08:37
categories: IT Programing
---
<p style="text-align:justify;"> O golang não emprementa a orientação a objetos por completo em seu contexto, ao contrario de outras linguagens como Java que tudo que é criado é uma classe, o golang é muito mais procedural do que orientada a objetos, porém podemos utilizar de alguns conceitos de orientação a objetos para implementação de softwares em golang.</p>

### Orientação a objetos

<p style="text-align: justify;"> Antes de falarmos diretamente sobre o golang é importante relembrar de alguns conceitos essenciais de orientção a o objetos, vamos lá.</p>

#### abstração 
<p style="text-align: justify"> A abstração e um dos pontos mais cruciais dentro de linguagens que implementam Orientação a Objetos, como estamos lidando com uma representação de um objeto real, é preciso imaginar o que esse objeto irá realizar dentro de nosso sistema. Existem três pontos importantes que precisam ser levados em consideração.</p>

#### Identidade
<p style="text-align: justify"> É preciso dar uma identidade ao objetos que criamos essa identidade deve ser unica dentro do sistema para evitar conflitos, devido a isso várias liguagens implementam o conceito de pacotes ou namespaces evitando assim que o objetos se repita dentro do pacote. </p>

#### Caracteristicas
<p style="text-align: justify"> No mundo real qualquer objeto possui elementos que o definem em orientação a objetos esses elementos são nomeados de propriedades ou atributos, por exemplo, um carro poderiater como propriedades cor, modelo, placa e valor. </p>



#### Ações dos objetos
<p style="text-align: justify"> Por fim é preciso definir as ações do objeto em questão essas ações dentro do mundo de orientação a onbjetos são chamados de de métodos, tomando como exemplo o objeto corro ele poderia implementar os metodos Ligar() Acelerar() Frear() e Desligar(), esses metodos vão possuir definido em seu interior todo o código para que eles funcionem de forma efetiva.</p>

<p style="text-align: justify;"> bem tendo relembrado isso podemos processeguir. Caso queiram mais detalhes podem ler esse <a href="https://www.devmedia.com.br/os-4-pilares-da-programacao-orientada-a-objetos/9264">artigo</a> da devimedia.com.br que foi de onde resumi grande parte das informações a respeito dos conceitos</p>


<p style="text-align:justify"> É importante saber que o golang  ao invés de utilizar classes para declaração de objetos compostos podemos utilizar structs, para criação desses objetos, vamos a um exemplo.</p>

<p style="text-align: justify;">  Em c# por exmplo para declararmos uma classe com seus metodos e atributos poderiamos fazer da seguinte maneira: </p>



```c#
    public class Carro
    {
        public string Modelo;
        public string Marca;
        public string Chassi;
        public string Fabricante;

        public void Ligar()
        {
            Console.WriteLine("Carro ligado!");
        }

        public void Desligar()
        {
            Console.WriteLine("Carro desligado!");
        }

        public void Acelerar()
        {
            Console.WriteLine("Carro acelerando...");
        }

        public void Frear()
        {
            Console.WriteLine("Carro freando...");
        }
    }


```

<p style="text-aling: justify"> Nesse exemplo temos uma classe que vai ser a base para nossos objetos, e nela temos seus atributos(caracteristicas) e seus métodos(Ações) isso quer dizer que todos os objetos criados a partir dessa classe vão possui os mesmos metodos e atributos. Então, como podemos criar um objeto a partir dessa classe? da seguinte maneira: </p>

```c#
    var objCarro = new Carro();
```
<p style="text-aling: justify"> Essa variavel objCarro possui acesso a todos os metodos e atributos da classe Carro. </p>

<p style="text-aling: justify"> Já em golang poderiamos facilmente fazer da seguinte forma:</p>

```golang
    type Carro struct {
        Modelo string
        Marca string
        Chaci string
        Fabricante string
    }

    func (c *Carro ) Ligar(){
        fmt.Println("Carro ligado!")
    }

    func (c *carro) Desligar(){
        fmt.Println("Carro desligado!")
    }

    func (c * Carro) Acelerar(){
        fmt.Println("Carro acelerando...")
    }
    
    func (c * Carro) Frear(){
        fmt.Println("Carro freando...")
    }
```