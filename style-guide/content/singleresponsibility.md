## Single Responsibility

Nós aplicamos o conceito de responsabilidade única para todos os componentes , serviços , html entre outros. isso nos ajuda
a manter o aplicativo mais limpo, fácil de ler e testar.

<ul>
	<li>Fazer: Definir uma coisa ( um serviço ou componente ) por aquivo.</li>
	<li>Considerar: limitar em no máximo 400 linhas de código por arquivo.</li>
	<li>Porque?: Um componente por arquivo deixa mais fácil de ler e evita problemas com o controle do código.</li>
	<li>Porque?: Um componente por arquivo esconde menos bugs, e deixa fácil para encontrar falhas.</li>
	<li>Porque?: Um componente por arquivo é mais fácil para ser exportado e facilita o carregamento lazy com o Router.</li>
</ul>

A chave é criar um código mais reusável, fácil de ler e menos propenso a erro.

A segui uma maneira errada de se implementar um componente object model Hero onde temos todo o código em um mesmo arquivo.

<b>app/heroes/hero.component.ts</b>
````typescript
/* avoid */
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { BrowserModule } from '@angular/platform-browser';
import { NgModule, Component, OnInit } from '@angular/core';
class Hero {
  id: number;
  name: string;
}
@Component({
  selector: 'my-app',
  template: `
      <h1>{{title}}</h1>
      <pre>{{heroes | json}}</pre>
    `,
  styleUrls: ['app/app.component.css']
})
class AppComponent implements OnInit {
  title = 'Tour of Heroes';
  heroes: Hero[] = [];
  ngOnInit() {
    getHeroes().then(heroes => this.heroes = heroes);
  }
}
@NgModule({
  imports: [ BrowserModule ],
  declarations: [ AppComponent ],
  exports: [ AppComponent ],
  bootstrap: [ AppComponent ]
})
export class AppModule { }
platformBrowserDynamic().bootstrapModule(AppModule);
const HEROES: Hero[] = [
  {id: 1, name: 'Bombasto'},
  {id: 2, name: 'Tornado'},
  {id: 3, name: 'Magneta'},
];
function getHeroes(): Promise<Hero[]> {
  return Promise.resolve(HEROES); // TODO: get hero data from the server;
}

````

Melhor é redistribuir em pequenas partes e cada uma ter uma única responsabilidade como no exemplo abaxio

<b>main.ts</b>
````typescript
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

import { AppModule }      from './app/app.module';

platformBrowserDynamic().bootstrapModule(AppModule);
````

<b>app/app.module.ts</b>
````typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { RouterModule } from '@angular/router';

import { AppComponent } from './app.component';
import { HeroesComponent } from './heroes/heroes.component';

@NgModule({
  imports: [
    BrowserModule,
  ],
  declarations: [
    AppComponent,
    HeroesComponent
  ],
  exports: [ AppComponent ],
  bootstrap: [ AppComponent ]
})

export class AppModule { }
````

<b>app/app.component.ts</b>
````typescript
import { Component } from '@angular/core';

import { HeroService } from './heroes';

@Component({
  moduleId: module.id,
  selector: 'toh-app',
  template: `
      <toh-heroes></toh-heroes>
    `,
  styleUrls: ['app.component.css'],
  providers: [ HeroService ]
})

export class AppComponent { }
````

<b>app/heroes/heroes/component.ts</b>
````typescript
import { Component, OnInit } from '@angular/core';

import { Hero, HeroService } from './shared';

@Component({
  selector: 'toh-heroes',
  template: `
      <pre>{{heroes | json}}</pre>
    `
})

export class HeroesComponent implements OnInit {
  heroes: Hero[] = [];
  constructor(private heroService: HeroService) {}
  ngOnInit() {
    this.heroService.getHeroes()
      .then(heroes => this.heroes = heroes);
  }
}
````

<b>app/heroes/shared/hero.service.ts</b>
````typescript
import { Injectable } from '@angular/core';

import { HEROES } from './mock-heroes';

@Injectable()
export class HeroService {
  getHeroes() {
    return Promise.resolve(HEROES);
  }
}
````

<b>app/heroes/shared/hero.model.ts</b>
````typescript
export class Hero {
  id: number;
  name: string;
}
````

<b>app/heroes/shared/mock-heroes.ts</b>
````typescript
import { Hero } from './hero.model';

export const HEROES: Hero[] = [
  {id: 1, name: 'Bombasto'},
  {id: 2, name: 'Tornado'},
  {id: 3, name: 'Magneta'},
];
````

<b>Funções pequenas</b>
<ul>
	<li>Fazer: Definir pequenas funções</li>
	<li>Considerar: limitar o número de linhas de código em no máximo 75</li>
	<li>Por quê: funções pequenas são mais fáceis de testar especialmente quando elas fazem uma coisa e tem um proposito.</li>
	<li>Por quê: funções pequenas promovem o reuso.</li>
	<li>Por quê: funções pequenas são mais fáceis de ler.</li>
	<li>Por quê: funções pequenas são mais fáceis de manter.</li>
	<li>Por quê: funções pequenas ajudam a evitar bugs escondidos.</li>
</ul>
