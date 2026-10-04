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
![](imagenes/binding/Sin%20título.jpg)
Se usa la notacion de bigote o doble llave
![](imagenes/binding/doble%20llave%20para%20binding.jpg)
para otros componentes se usa corchetes 
![](imagenes/binding/corchetes.png)

el resultado es 
![alt text](image.png)

## 2. Eventos

Se agrega la variable y la funcion para el evento
![](imagenes/Eventos/class.jpg)

Se manda a llamar el evento desde el html
![](imagenes/Eventos/htm.jpg)

Esto da como resultado que al dar click al titulo suma 1

![](imagenes/Eventos/Resultado.jpg)

## 3. Vinculo de datos bidireccional
double data binding es para que pueda modificar desde otro componente

[()] ==> banana in a box sintaxis 
[] ==> obtener informacion del ts al html
() ==> para los eventos, en este caso html a ts

se importa FormsModule
![](imagenes/03%20binding%20bidireccional/FormsModule.jpg)
se agrega ngModel
![](imagenes/03%20binding%20bidireccional/Sin%20título.jpg)

da como resultado
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
