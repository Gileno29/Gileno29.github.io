---
layout: post
title:  "Orientação a Objetos em golang"
date:   2023-09-17 08:37
categories: IT Programing
---
<p style="text-align:justify;"> O golang não emprementa a orientação a objetos por completo em seu contexto, ao contrario de outras linguagens como Java que tudo que é criado é uma classe, o golang é muito mais procedural do que orientada a objetos, porém podemos utilizar de alguns conceitos de orientação a objetos para implementação de softwares em golang.</p>

<p style="text-aling:justify"> É importante saber que o golang  ao invés de utilizar classes para declaração de objetos compostos podemos utilizar structs, para criação desses objetos, vamos a um exemplo.</p>

<p style="text-aling: justify;">  Em c# por exmplo para declararmos uma classe com seus metodos e atributos poderiamos fazer da seguinte maneira: </p>

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