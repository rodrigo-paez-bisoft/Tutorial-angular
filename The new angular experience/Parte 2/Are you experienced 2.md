# Angular parte 2

## 10. Constructores

![alt text](imagenes/10%20Constructor/ejemplo%20constructor.jpg)

Así de sencillo es el metodo constructor

## 11. Models

La razon de los models es que cuando inicializas un constructor a veces necesitas un tipo de objeto como en este caso los product, pero en este caso solo esta infiriendo los tipos y son datos no estructurados
![alt text](imagenes/11%20Models/Problematica.png)

por lo cual se necesita para poder tipar esos objetos, hacer un modelo

![alt text](imagenes/11%20Models/Interfaz.png)

ese es la sintaxis basica para las interfaces 
![alt text](imagenes/11%20Models/sintaxis-ts.png)

## 12. ngClass
La directiva ngClass nos permite crear clases dinamicas y dar estilos a los proyectos segun se cumplan algunas condiciones

![alt text](imagenes/12%20ngClass/ngClass-ts.png)

primero se importa NgClass.

ahora para usar el ngClass se usara de ejemplo hacer una etiqueta que cambie a modo oscuro, se crea el boolean isDarkMode, despues la funcion toggleDarkMode.

el estilo cambia a la clase que se da en css con la siguientes propiedades <br>
![alt text](image.png)

![alt text](image-1.png)
ahora en la etiqueta h2 se coloca el ngClass y la propiedad de css que cambia y la propiedad ts que evalua {css: ts}.

para disparar el evento se configura un boton que al hacer click ejecute el metodo toggleDarkMode definido en el ts

<br>
para cambiar un poco las cosas tambien se integra este caso donde solo se hace grande el texto con fines de experimentar

```ts
isBigMode: boolean = true;
toggleBigMode(){
    this.isBigMode = !this.isBigMode;
}
```

```html
<button (click)="toggleBigMode()">Toggle Big Mode</button>
```

## 13. Formularios reactivos

Los formularios reactivos son formularios administrados principalmente desde TypeScript. Angular representa cada campo con clases como:

* ``FormControl:`` controla un campo individual.
* ``FormGroup:`` agrupa varios controles y representa el formulario completo.
 
 
Lo que se tiene que importar
```ts
import { FormControl, FormGroup, ReactiveFormsModule } from '@angular/forms';
  imports: [ReactiveFormsModule],
```

```ts
movieForm: FormGroup;
name: FormControl;
duration: FormControl;
director: FormControl;
```

Cada ``FormControl`` guarda el valor actual de su campo, además de su estado


aqui se inicializa
```ts 
constructor() {
    this.name = new FormControl('');
    this.duration = new FormControl('');
    this.director = new FormControl('');
    
    this.movieForm = new FormGroup({
      name: this.name,
      duration: this.duration,
      director: this.director,
    });
  }
```
Este metodo manda la respuesta a la consola

```ts
handdleSubmit(): void {
console.log(this.movieForm.value);
}
```
Estos son los campos para ingresar los atributos
```html
<app-header></app-header>
<form [formGroup]="movieForm" class="movie-form" (submit)="handdleSubmit()">
  <fieldset>
    <label for="field-name">movie name</label>
    <input type="text" id="field-name" formControlName="name">
  </fieldset>
  <fieldset>
    <label for="field-duration">movie duration</label>
    <input type="text" id="field-duration" formControlName="duration">
  </fieldset>
  <fieldset>
    <label for="field-director">movie director</label>
    <input type="text" id="field-director" formControlName="director">
  </fieldset>
<fieldset>
    <button type="submit" id="submit">Submit</button>
  </fieldset>
</form>
```

Este es el estilo 

```css
.movie-form{
    margin: 20px;
  
}
fieldset{
    margin: 10px;
    border: 5px solid black;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
}
input{
    margin: 10px;
}
#submit{
    margin: 10px;
}
```
## 14. Validators

Se importa
```ts
import { FormControl, FormGroup, ReactiveFormsModule, Validators } from '@angular/forms';
```

```ts
this.name = new FormControl('',Validators.required);
    this.duration = new FormControl('',[Validators.required,Validators.min(1),Validators.max(500)]);
    this.director = new FormControl('',Validators.required);
```
se puede bloquear el boton 
```html
<fieldset>
    <button type="submit" id="submit" [disabled]="movieForm.invalid">Submit</button>
  </fieldset>
</form>
```

algunos cambios para mejorar
```ts
handdleSubmit(): void {
    console.log(this.movieForm.value);
    this.movieForm.reset();
  }
```

estilo
```css
.form-error{
    color: red;
    font-size: 12px;
}
```
La primera condicion del primer textfield
```html
  <fieldset>
    <label for="field-name">movie name</label>
    <input type="text" id="field-name" formControlName="name">
    @if (name.invalid && name.touched) {
      <p class="form-error">name is required</p>
    }
  </fieldset>

 ```
 Una condicion mas especifica
 ```html 
  <fieldset>
    <label for="field-duration">movie duration</label>
    <input type="text" id="field-duration" formControlName="duration">
    @if(duration.hasError("required") && duration.touched) {
      <p class="form-error">duration is required</p>
    }@else if (duration.hasError("max") && duration.touched) {
      <p class="form-error">duration must be less than 500</p>
    }@else if (duration.hasError("min") && duration.touched) {
      <p class="form-error">duration must be greater than 1</p>
    }
  </fieldset>
```
bloquear el boton cuando hay errores
```html
<fieldset>
    <button type="submit" id="submit" [disabled]="movieForm.invalid">Submit</button>
  </fieldset>
</form>
```
## 15. Services


primero se crea la carpeta services
```ts
import {Injectable} from '@angular/core';
import Product from '../Models/Product';

@Injectable({
  providedIn: 'root'
})
export class ProductService {
  product: Product ;
  constructor() {
    this.product = {
      name: 'Computer',
      price: 99.99,
      isAvailable: true
    };
  }
  setProductName(name: string): void {
    this.product.name = name;
  }
}
```

y esto se hace en los componentes hijos

```ts
export class Child {
  constructor(public productService: ProductService) {}
}
```
y el html
```html
<div class="component">
  <h2>Componente Hijo 1</h2>
  <h3>
      {{productService.product.name}}
      {{productService.product.price}}
</h3>
</div>
```
el estilo es el siguiente

```css
.component{
    margin: 10px;
    border: 5px solid black;
    border-radius: 5px;
    display: flex;
    flex-direction: column; 
    justify-content: center;
    align-items: center;
    padding: 10px;
}
```

para darle un poco mas de complejidad y hacer otro tipo de evento

```html
<div class="component">
  <h2>Componente Hijo 2</h2>
  <h3>{{productService.product.name}}</h3>
  <button (click)="productService.setProductName('Television')">Set Product Name</button>
</div>
```