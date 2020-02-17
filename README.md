
## Instalación

Se necesita tener instalado:
* [NodeJS](https://nodejs.org/es/) >12
    * `node -v`: verificar versión instalada.
    * `npm -v`: verrificar versión instalada.
* [Angular CLI](https://cli.angular.io/) >8
    * `npm install -g @angular/cli`: Instalar 
    CLI Angular.
    * `ng version`: Versión de Angular.
* Visual Studio Code:
    * Angular Language Service.
    * TSLint


## Comandos Angular

* `ng new [Nombre de proyecto]`: Crear un nuevo proyecto angular.
    * Routing: Si
    * Proprocesador: SCSS (Sass)
* `ng serve`: Iniciar servidor Angular De **DESARROLLO**
    * `http://localhost:4200/`
* `ng build --prod`: Iniciar servidor Angular en **PROCUCCIÓN**

## Archivos:

* `[Proyecto]/src/app/app.componet.html`: Html Principal.
* `[Proyecto]/src/app/app.componet.ts`: Archivo que define Componente (HTML y CSS)
    * Definir Funciones:
        ```
        addItem(){
            this.nombres.push('Nuevo item');
        }
        ```
* `[Proyecto]/src/app/app.module.ts`: Agregar nuevos paquetes.  
    ```
    import { FormsModule } from '@angular/forms';

    @NgModule({
    imports: [
        FormsModule
    ]
    })
    ```
* `[Proyecto]/src/app/[Modelo].model.ts`: Archivo donde se define una **INTERFACE**.
    ```
    export interface Product {
        id:String;
        title:string;
        image:string;
        price:number;
        description:string;
    }
    ```

## Lenguaje Angular:

* **String Interpolation**:
    * ` {{ [JS] }}`: Puede ser un String, una variable o una operación en JS
* **Data binding**
    * `[()]`: *two-ways biding*, mecanismo que actualiza la vista y el modelo al mismo tiempo.

*`<input type="text" [(ngModel)]="[Variable]]">`*

* *\*ngIf*: Condicional, Se puede utilizar para ocultar y mostrar elementos.
    ```
    <div *ngIf="title === 'David'">
        Esto es un div
    </div>
    ```

* \*ngFor: Recorrer una lista:
    * ; index as i

    ```
    <ul>
    <li *ngFor="let nombre of nombres; index as i">
        {{ nombre }} {{ i }}
    </li>
    </ul>
    ```
* Ejecutar Funciones mediante eventos:
    * `<button (click)="addItem()"> Agregar Item </button>
      `

* Definir un Array con un tipo(interface):
    ```
    import { Product } from './product.model';
    products: Product []= [
        {},
        {}
    ];
    ```


