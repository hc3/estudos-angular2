# Material de estudo para o angular2

Estudos baseados no curso de [angular2]() da Loiane Groner se você ainda não conhece vale a pena assistir as aulas.

### **Aula 01 ** Introdução

Algumas informações básicas sobre o framework:
<ul>
    <li>https://angular.io</li>
    <li>Parceria Google + Microsoft</li>
    <li>Open Source código no github</li>
    <li>Atualmente na versão RC </li>
    <li>Não é continuação da versão 1</li>
    <li>Foi reescrito</li>
    <li>Uso de padrões web e web components</li>
</ul>

Blocos principais:
<ul>
    <li>Components</li>
    <li>Diretivas</li>
    <li>Roteamento</li>
    <li>Serviços</li>
    <li>Template</li>
    <li>Metadata</li>
    <li>Data Binding</li>
    <li>Injeção de Dependência</li>
</ul>

#### Component {}

Encapsula:
<ul>
    <li>Template</li>
    <li>Metadata: processamento das classes</li>
    <li>Dado a ser mostrado na tela (Data Binding)</li>
    <li>Comportamento da VIEW</li>
</ul>

quando criamos aplicações com angular2, vai ser tudo orientado a componentes todos vão estar atrelados a um component root ( raiz ), o principal objetivo
do component é exibir dados, e para isso precisamos de um back end que pode ser em qualquer linguagem e é claro que não é de bom tom escrever código de lógica
de negócio e comunicação com o back end no component e para isso vamos ter o **serviço** que podera ser injetado em outras clases, para isso vamos usar a injeção de
dependência do angular2, vamos usar o **router** para trocar as telas ou views o responsável por modificar elementos DOM ou seu comportamento vai ser a **diretiva**


### **Aula 02 ** Ambiente de desenvolvimento

vamos precisar do node.js e o typescript e para instalar o typescript vamos usar o npm _npm install -g typescript_ , o typescript é um super conjunto do javascript.
vamos precisar também instalar o _npm install -g typings_ é um conjunto para desenvolver com angular2.

### **Aula 03 ** Primeira app Hello, World!

para criar aplicações com o angular2 vamos usar o npm com _npm install -g angular-cli_

### **Aula 04 ** Entendendo a primeira app Hello, World!


### **Aula 05 ** Criando um component

Criando o primeiro component, a criação de um component no angualar2 consiste em criar uma pasta para o component essa pasta é conhecida como módulo, e nela vão estar os serviços, o component entre outros que podemos precisar, a nomenclatura dos components é outra coisa importante vamos ter o <nome>.<tipo>.ts
exemplo : MeuPrimeiro.component.ts
````
import { Component } from '@angular/core';


@Component({
  selector: 'meu-primeiro-component',
  template:'<h2>Hellow World</h2>'
})

export class MeuPrimeiroComponent {}

````

````
import { Component } from '@angular/core';

import { MeuPrimeiroComponent } from './primeiro/meu-primeiro.component';

@Component({
    selector: 'my-app',
    template: `
        <h1>Angular 2 Boilerplate</h1>
        <p>Hello World!</p>
        <meu-primeiro-component></meu-primeiro-component>
    `,
    directives: [MeuPrimeiroComponent]
})
export class AppComponent { }
````

dica para criar component no angular2 segui o CIDAR
<ul>
  <li>Class (Criar a classe)</li>
  <li>Import</li>
  <li>Decorate (Decorar a classe)</li>
  <li>Alterar</li>
  <li>Repetir</li>
</ul>


### **Aula 06 ** Template

vamos agora seguir o CIDAR para exemplificar :
C - Criar classe.
````
export class CursosComponent {

}
````

I - import
````
import { Component } from '@angular/core';
````

D - Decorate
````
@Component({
  selector: 'cursos-lista',
  template:`
    <p>Olá</p>
  `
})
````

A - Alterar
````typescript
import { Component } from '@angular/core';

@Component({
  moduleId: module.id,
  selector: 'cursos-lista',
  templateUrl:'cursos.component.html'
})

export class CursosComponent {

    nome = 'Eliel';

    cursos = ['Angular2', 'Java', 'Javascript'];
}
````

R - Repetir
podemos fazer o mesmo processo para todos os outros componentes que forem sendo criados.


### **Aula 07 ** Serviços e DI ( Injeção de dependência )

Os serviços são a ponte entre o servidor e o component, por muitas vezes precisamos fazer uma requisição para um servidor e retornar dados os serviços são os responsáveis por isso.
