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