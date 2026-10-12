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
Se usa la notacion de bigote o doble llave
![](imagenes/01%20binding/doble%20llave%20para%20binding.jpg)
para otros componentes se usa corchetes 
![](imagenes/01%20binding/corchetes.png)

el resultado es 
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

## if

Se agrega una condicion booleana al ts

![](imagenes/04%20if/boolean.png)

Se pone el if en el html para que evalue
![](imagenes/04%20if/if.png)

resultado
![](imagenes/04%20if/resultado.jpg)

## for
Los bucles for son muy sencillos son igual que el if

![](imagenes/05%20for/ts.jpg)

![](imagenes/05%20for/html.jpg)

![](imagenes/05%20for/resultado.png)

## componentes hijos

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
## Signals

Funciona exactamente como Input, con la diferencia que tiene mejor 

![](imagenes/07%20Input%20signals/signals.jpg)

## Output

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
## Output signal

para este solo se cambia el componente y se importa output<br>
![](imagenes/08%20Output/output%20signal.png)
