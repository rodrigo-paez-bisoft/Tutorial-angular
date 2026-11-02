# Angular

### comandos
para crear el entorno

* npm install -g @angular/cli
* ng version
* ng new mi-proyecto

para crear componentes

* ng g c Components/

## 1. data binding
Se crea la variable 
![](imagenes/01%20binding/Sin%20título.jpg)
Se usa la notacion de bigote o doble llave <br>
![](imagenes/01%20binding/doble%20llave%20para%20binding.jpg)
para otros componentes se usa corchetes 
![](imagenes/01%20binding/corchetes.png)

el resultado es <br>

![alt text](imagenes/01%20binding/resultado.png)

## 2. Eventos

Se agrega la variable y la funcion para el evento
![](imagenes/02%20Eventos/class.jpg)

Se manda a llamar el evento desde el html
![](imagenes/02%20Eventos/htm.jpg)

Esto da como resultado que al dar click al titulo suma 1

![](imagenes/02%20Eventos/Resultado.jpg)

## 3. Vinculo de datos bidireccional
double data binding es para que pueda modificar desde otro componente

[()] ==> banana in a box sintaxis <br>
[] ==> obtener informacion del ts al html<br>
() ==> para los eventos, en este caso html a ts

se importa FormsModule
![](imagenes/03%20binding%20bidireccional/FormsModule.jpg)
se agrega ngModel
![](imagenes/03%20binding%20bidireccional/Sin%20título.jpg)

da como resultado <br>
![](imagenes/03%20binding%20bidireccional/resultado.jpg)

## 4. if

Se agrega una condicion booleana al ts

![](imagenes/04%20if/boolean.png)

Se pone el if en el html para que evalue
![](imagenes/04%20if/if.png)

resultado
![](imagenes/04%20if/resultado.jpg)

## 5. for
Los bucles for son muy sencillos son igual que el if

![](imagenes/05%20for/ts.jpg)

![](imagenes/05%20for/html.jpg)

![](imagenes/05%20for/resultado.png)

## 6. Input
Componentes hijos <br>
primero se crea el componente
![](imagenes/06%20input%20padre-hijo/crear%20componente.jpg)

despues se importa input
![](imagenes/06%20input%20padre-hijo/input%20child.jpg)

se agregan los cambios al componente hijo
![](imagenes/06%20input%20padre-hijo/html%20child.jpg)

se incorpora al ts padre
![](imagenes/06%20input%20padre-hijo/ts%20padre.jpg)

y se incorpora al html
![](imagenes/06%20input%20padre-hijo/html%20padre.jpg)

![](imagenes/06%20input%20padre-hijo/Person.jpg)
![](imagenes/06%20input%20padre-hijo/persona.jpg)
## 7. Signals

Funciona exactamente como Input, con la diferencia que tiene mejor 
![](imagenes/07%20Input%20signals/signals.jpg)

### para aumentar la dificultad se integro con un ciclo for

Primero se agrega una interfaz para el objeto Person
![](imagenes/07%20Input%20signals/Interfaz%20person.jpg)
En esta imagen se agrego dos objetos de la interfaz person, se adapto el signal para el array
![](imagenes/07%20Input%20signals/app%20signals%20for.jpg)
Al typescript del hijo se le declaro el arreglo vacio con input, se arregla required para pueda tomar la interfaz
![](imagenes/07%20Input%20signals/child%20type%20signals%20for.jpg)
Aqui se integra el ciclo for, de manera muy sencilla, solo hay que tener cuidado con los ()
![](imagenes/07%20Input%20signals/child%20html%20signals%20for.jpg)
por ultimo se agrega en el html la propiedad para mandar a llamar el array y las signals
![](imagenes/07%20Input%20signals/app%20html%20signals%20for.jpg)
## 8. Output

para el Output primero se configura el componente

en este caso se configura hijo

![](imagenes/08%20Output/Hijo.jpg)
se importa Output y EvenEmitter, se coloca el decorador de Output, se pone el nombre y el tipo, este caso se pone "any" del tipo EventEmitter y se crea una instacia de el.

![](imagenes/08%20Output/app.jpg) <br>
aqui solo se crea la variable y una funcion para cambiar la cadena

![](imagenes/08%20Output/childpage2.jpg)

aqui en html y ts, userName es el que manda a llamar y el evento HandlerLogin es el que manda a llamar cuando se ejecuta el evento click.
![](imagenes/08%20Output/padrepage2.jpg)
en h2 se manda a llamar el name y cuando se ejecuta el boton se ejecuta la funcion setName

### Algunas modificaciones de estilo

```css
.child-component {
    margin: 10px;
    border: 5px solid black;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 10px;
}
button {
    margin-top: 10px;
    padding: 5px 10px;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
}
```
### modificaciones al Child component ts

Este codigo lo que hace es permitir el logout
```ts
 @Output()
  login = new EventEmitter<string>();
  @Output()
  logout = new EventEmitter<void>();

  handleLogin() {
    this.login.emit(this.userName);
  }

  handleLogout() {
    this.logout.emit();
  }
```
### Componente Child.html
Se manda llamar los eventos
```html
<div class="child-component">
    <h2>Este es un componente hijo</h2>
    <p>Nombre: {{ userName }}</p>
    <button (click)="handleLogin()">Iniciar sesión</button>
    <button (click)="handleLogout()">Cerrar sesión</button>
</div>
```
### Modificaciones al archivo app.ts
se creo la variable booleana isLoggedIn y dos funciones setName y toggleLogin
```ts
name: string ="";
  isLoggedIn: boolean = false;
  setName(e: string) {
    this.name = e;
    this.isLoggedIn = true;
  }
  toggleLogin() {
    this.isLoggedIn = false;
  }
```
### modificaciones al archivo app.html
```html
@if (isLoggedIn) {
    <h2>Welcome, {{ name }}</h2>
} @else {
    <h2>Please log in</h2>
}
<app-child (login)="setName($event)" (logout)="toggleLogin()"></app-child>
```
## 9. Output signal

para este solo se cambia el componente y se importa output<br>
![](imagenes/08%20Output/output%20signal.png)

El resultado es <br>

![](imagenes/08%20Output/resultadoOutput.jpg)

Al dar click en el boton login aparece la cadena que dispara userName

### Modificaciones
aqui solo se cambio a output que así funciona signals
```ts
import { Component, EventEmitter, output } from '@angular/core';

    login = output<any>();
    logout = output<void>();
  handleLogin() {
    this.login.emit(this.userName);
  }

  handleLogout() {
    this.logout.emit();
  }
```