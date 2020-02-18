
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

* `[Proyecto]/src/app/app.component.html`: Html Principal.
    * Llamar a un componente:  
    `<app-product></app-product>`

* `[Proyecto]/src/app/app.component.ts`: Archivo que define Componente (HTML y CSS)
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
Nuevo componente.
```
import { ProductComponent } from './components/product.component';

declarations: [
    AppComponent,
    ProductComponent
  ]

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
* `[Proyecto]/src/app/Components/product.component.ts`: Crear un componente.

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

* **Componentes**

Un componente es la parte más pequeña de una aplicación web.

```
import { Component } from '@angular/core';

@Component({
    selector: 'app-product',
    templateUrl: './product.component.html'
})

export class ProductComponent{

}
```

## Inputs y Outputs: 
Enviar y recibir datos desde un componente

* Input:
Se define dentro de un componente se importa:  
`import { Input } from '@angular/core';`
y se utiliza en varibles al cual se vamos asignar un valor:  
`@Input() product: Product;`

*HTML Principal:  
`<app-product [product]="product"></app-product>`

* Output: 
Se define dentro de un componente se importa:  
`import { Output, EventEmitter} from '@angular/core';`
Declaramos el evento:
`@Output() ProductClicked: EventEmitter<any> = new EventEmitter();`
Leerlo desde el componente padre (Html principal):
`<app-product (ProductClicked)="clickProduct($event)"></app-product>`

## Ciclo de vida de los componentes

Archivo: product.component.ts (Se define una clase)

1. Constructor: Se ejecuta primero, cada vez que se crea una instancia de la clase
```
    constructor(){
        console.log("1. Constructor");
        
    }
```
2. ngOnChanges: Detecta los cambios del componente.

```
import { OnChanges, SimpleChange  } from '@angular/core';

export class ProductComponent implements OnChanges{
    ngOnchanges(changes:){

    }
};
```

