# Angular parte 3
## 16. Router

primero se crean las rutas, por ejemplo en este caso se van a crear dos pages

en este caso se maneja pages porque lo que se pretende hacer con routers es que se puedan mover por paths que es sencillamente que en el url se pueda agregar un nombre para que mueva la página, esto se esclarece cuando ponga los ejemplos

```ts
import { Routes } from '@angular/router';
import { HomeComponent } from './Pages/home/home';
import { MovieFormComponent } from './Pages/movie-form-page/movie-form';
import { MovieListComponent } from './Pages/movie-list/movie-list';
export const routes: Routes = [
    {path: '',component: HomeComponent},
    {path: 'movies', component: MovieListComponent},
    {path: 'create',component: MovieFormComponent},
];

```
## 17.RouterLink

Para este caso se ha modificado el header de la siguiente manera

```html
<main>
    <header>
        <img src="/logo.svg" alt="aqui va el logo">
    </header>
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/movies">Movies</a></li>
        <li><a href="/create">Create Movie</a></li>
    </ul>
</main>
```
y con el estilo de:

```css
main{
    margin: 10px;
    border: 5px solid black;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 10px;
}

header {
    width: 100%;
    display: flex;
    justify-content: center;
}

ul{
    list-style-type: none;
    width: 100%;
    margin: 10px 0 0;
    padding: 0;
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    gap: 10px;
}

ul li:nth-child(1) {
    justify-self: start;
}

ul li:nth-child(2) {
    justify-self: center;
}

ul li:nth-child(3) {
    justify-self: end;
}
```
