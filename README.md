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

para criar aplicações com o angular2 existem duas formas usando o npm com _npm install -g angular-cli_ e a outra forma é 
