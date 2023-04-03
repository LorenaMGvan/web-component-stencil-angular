# Integrar web component stencil en Angular
##### 1.  Hacer login y publicar tu componente de stencil

`npm login` *te solicitara tu correo

`npm publish –-access public`


##### 2.  Instalar nuestro web component con npm
   `npm install boton-prueba --save`
    
##### 3. Abrir proyecto Angular y editar el archivo app.module.ts
colocar las siguientes linea:
`import 'boton-prueba'`

b) añadir lo siguiente:
`import { CUSTOM_ELEMENTS_SCHEMA, NgModule } from '@angular/core';`

`  schemas: [CUSTOM_ELEMENTS_SCHEMA]`

ejemplo del archivo app.module.ts:
```javascript
import { CUSTOM_ELEMENTS_SCHEMA, NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import 'boton-prueba';
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';


@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  providers: [],
  schemas: [CUSTOM_ELEMENTS_SCHEMA], // here is the schema declaration to add
  bootstrap: [AppComponent]
})
export class AppModule { }


```
##### 4. Abrir el archivo main.ts

añadir esta linea:
`import { defineCustomElements } from 'boton-prueba/loader';`

`defineCustomElements(window);`


```javascript

import { defineCustomElements } from 'boton-prueba/loader'; // add this line

import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

import { AppModule } from './app/app.module';


platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));

  defineCustomElements(window); // call the function here
```

##### 5. Abrir el archivo app.component.html

```javascript
<at-button text="hola mundo!">
</at-button>
<router-outlet></router-outlet>


```




This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 15.1.4.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
