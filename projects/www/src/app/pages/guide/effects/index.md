# @ngrx/effects

Effects are an RxJS powered side effect model for [Store](guide/store). Effects use streams to provide [new sources](https://martinfowler.com/eaaDev/EventSourcing.html) of actions to reduce state based on external interactions such as network requests, web socket messages and time-based events.

## Introduction

In a service-based Angular application, components are responsible for interacting with external resources directly through services. Instead, effects provide a way to interact with those services and isolate them from the components. Effects are where you handle tasks such as fetching data, long-running tasks that produce multiple events, and other external interactions where your components don't need explicit knowledge of these interactions.

## Key Concepts

- Effects isolate side effects from components, allowing for more _pure_ components that select state and dispatch actions.
- Effects are long-running services that listen to an observable of _every_ action dispatched from the [Store](guide/store).
- Effects filter those actions based on the type of action they are interested in. This is done by using an operator.
- Effects perform tasks, which are synchronous or asynchronous and return a new action.

## Installation

Detailed installation instructions can be found on the [Installation](guide/effects/install) page.

## Comparison with Component-Based Side Effects

In a service-based application, your components interact with data through many different services that expose data through properties and methods. These services may depend on other services that manage other sets of data. Your components consume these services to perform tasks, giving your components many responsibilities.

Imagine that your application manages movies. Here is a component that fetches and displays a list of movies.

<ngrx-code-example header="movies-page.component.ts">

```ts
import { Component, inject, OnInit } from '@angular/core';
import { CommonModule } from '@angular/common';

@Component({
  template: `
    <li *ngFor="let movie of movies">
      {{ movie.name }}
    </li>
  `,
  imports: [CommonModule],
})
export class MoviesPageComponent implements OnInit {
  private moviesService = inject(MoviesService);
  protected movies: Movie[] = [];

  ngOnInit() {
    this.movieService
      .getAll()
      .subscribe((movies) => (this.movies = movies));
  }
}
```

</ngrx-code-example>

You also have the corresponding service that handles the fetching of movies.

<ngrx-code-example header="movies.service.ts">

```ts
import { Injectable, inject } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root',
})
export class MoviesService {
  private http = inject(HttpClient);

  getAll(): Observable<Movie[]> {
    return this.http.get<Movie[]>('/movies');
  }
}
```

</ngrx-code-example>

The component has multiple responsibilities:

- Managing the _state_ of the movies.
- Using the service to perform a _side effect_, reaching out to an external API to fetch the movies.
- Changing the _state_ of the movies within the component.

`Effects` when used along with `Store`, decrease the responsibility of the component. In a larger application, this becomes more important because you have multiple sources of data, with multiple services required to fetch those pieces of data, and services potentially relying on other services.

Effects handle external data and interactions, allowing your services to be less stateful and only perform tasks related to external interactions. Next, refactor the component to put the shared movie data in the `Store`. Effects handle the fetching of movie data.

<ngrx-code-example header="movies-page.component.ts">

```ts
import { Component, inject, OnInit } from '@angular/core';
import { CommonModule } from '@angular/common';

@Component({
  template: `
    <div *ngFor="let movie of movies$ | async">
      {{ movie.name }}
    </div>
  `,
  imports: [CommonModule],
})
export class MoviesPageComponent implements OnInit {
  private store = inject(Store<{ movies: Movie[] }>);
  protected movies$ = this.store.select((state) => state.movies);

  ngOnInit() {
    this.store.dispatch({ type: '[Movies Page] Load Movies' });
  }
}
```

</ngrx-code-example>

The movies are still fetched through the `MoviesService`, but the component is no longer concerned with how the movies are fetched and loaded. It's only responsible for declaring its _intent_ to load movies and using selectors to access movie list data. Effects are where the asynchronous activity of fetching movies happens. Your component becomes easier to test and less responsible for the data it needs.

## Writing Effects

To isolate side effects from your component, you can create NgRx effects to listen for events and perform tasks.

Effects are injectable service classes with distinct parts:

- An injectable `Actions` service that provides an observable stream of _each_ action dispatched _after_ the latest state has been reduced.
- Metadata is attached to the observable streams using the `createEffect` function. The metadata is used to register the streams that are subscribed to the store. Any action returned from the effect stream is then dispatched back to the `Store`.
- Actions are filtered using a pipeable [`ofType` operator](guide/effects/operators#oftype). The `ofType` operator takes one or more action types as arguments to filter on which actions to act upon.
- Effects are subscribed to the `Store` observable.
- Services are injected into effects to interact with external APIs and handle streams.

<ngrx-docs-alert type="help">

**Note:** Since NgRx v15.2, classes are not required to create effects. Learn more about functional effects [here](#functional-effects).

</ngrx-docs-alert>

To show how you handle loading movies from the example above, let's look at `MoviesEffects`.

<ngrx-code-example header="movies.effects.ts">

```ts
import { Injectable, inject } from '@angular/core';
import { Actions, createEffect, ofType } from '@ngrx/effects';
import { EMPTY } from 'rxjs';
import { map, exhaustMap, catchError } from 'rxjs/operators';
import { MoviesService } from './movies.service';

@Injectable()
export class MoviesEffects {
  private actions$ = inject(Actions);
  private moviesService = inject(MoviesService);

  loadMovies$ = createEffect(() => {
    return this.actions$.pipe(
      ofType('[Movies Page] Load Movies'),
      exhaustMap(() =>
        this.moviesService.getAll().pipe(
          map((movies) => ({
            type: '[Movies API] Movies Loaded Success',
            payload: movies,
          })),
          catchError(() => EMPTY)
        )
      )
    );
  });
}
```

</ngrx-code-example>

The `loadMovies$` effect is listening for all dispatched actions through the `Actions` stream, but is only interested in the `[Movies Page] Load Movies` event using the `ofType` operator. The stream of actions is then flattened and mapped into a new observable using the `exhaustMap` operator. The `MoviesService#getAll()` method returns an observable that maps the movies to a new action on success, and currently returns an empty observable if an error occurs. The action is dispatched to the `Store` where it can be handled by reducers when a state change is needed. It's also important to [handle errors](#handling-errors) when dealing with observable streams so that the effects continue running.

<ngrx-docs-alert type="inform">

**Note:** Event streams are not limited to dispatched actions, but can be _any_ observable that produces new actions, such as observables from the Angular Router, observables created from browser events, and other observable streams.

</ngrx-docs-alert>

## Handling Errors

Effects are built on top of observable streams provided by RxJS. Effects are listeners of observable streams that continue until an error or completion occurs. In order for effects to continue running in the event of an error in the observable, or completion of the observable stream, they must be nested within a "flattening" operator, such as `mergeMap`, `concatMap`, `exhaustMap`, and `switchMap`. The example below shows the `loadMovies$` effect handling errors when fetching movies.

<ngrx-code-example header="movies.effects.ts">

```ts
import { Injectable, inject } from '@angular/core';
import { Actions, createEffect, ofType } from '@ngrx/effects';
import { of } from 'rxjs';
import { map, exhaustMap, catchError } from 'rxjs/operators';
import { MoviesService } from './movies.service';

@Injectable()
export class MoviesEffects {
  private actions$ = inject(Actions);
  private moviesService = inject(MoviesService);

  loadMovies$ = createEffect(() => {
    return this.actions$.pipe(
      ofType('[Movies Page] Load Movies'),
      exhaustMap(() =>
        this.moviesService.getAll().pipe(
          map((movies) => ({
            type: '[Movies API] Movies Loaded Success',
            payload: movies,
          })),
          catchError(() =>
            of({ type: '[Movies API] Movies Loaded Error' })
          )
        )
      )
    );
  });
}
```

</ngrx-code-example>

The `loadMovies$` effect returns a new observable in case an error occurs while fetching movies. The inner observable handles any errors or completions and returns a new observable so that the outer stream does not die. You still use the `catchError` operator to handle error events, but return an observable of a new action that is dispatched to the `Store`.

## Functional Effects

Functional effects are also created by using the `createEffect` function. They provide the ability to create effects outside the effect classes.

To create a functional effect, add the `functional: true` flag to the effect config. Then, to inject services into the effect, use the [`inject` function](https://angular.dev/api/core/inject).

<ngrx-code-example header="actors.effects.ts">

```ts
import { inject } from '@angular/core';
import { catchError, exhaustMap, map, of, tap } from 'rxjs';
import { Actions, createEffect, ofType } from '@ngrx/effects';

import { ActorsService } from './actors.service';
import { ActorsPageActions } from './actors-page.actions';
import { ActorsApiActions } from './actors-api.actions';

export const loadActors = createEffect(
  (
    actions$ = inject(Actions),
    actorsService = inject(ActorsService)
  ) => {
    return actions$.pipe(
      ofType(ActorsPageActions.opened),
      exhaustMap(() =>
        actorsService.getAll().pipe(
          map((actors) =>
            ActorsApiActions.actorsLoadedSuccess({ actors })
          ),
          catchError((error: { message: string }) =>
            of(
              ActorsApiActions.actorsLoadedFailure({
                errorMsg: error.message,
              })
            )
          )
        )
      )
    );
  },
  { functional: true }
);

export const displayErrorAlert = createEffect(
  () => {
    return inject(Actions).pipe(
      ofType(ActorsApiActions.actorsLoadedFailure),
      tap(({ errorMsg }) => alert(errorMsg))
    );
  },
  { functional: true, dispatch: false }
);
```

</ngrx-code-example>

<ngrx-docs-alert type="inform">

It's recommended to inject all dependencies as effect function arguments for easier testing. However, it's also possible to inject dependencies in the effect function body. In that case, the [`inject` function](https://angular.dev/api/core/inject) must be called within the synchronous context.

</ngrx-docs-alert>

## Registering Effects

Effect classes and functional effects are registered using the `provideEffects` method.

At the root level, effects are registered in the `providers` array of the application configuration.

<ngrx-docs-alert type="inform">

Effects start running **immediately** after instantiation to ensure they are listening for all relevant actions as soon as possible.
Services used in root-level effects are **not** recommended to be used with services that are used with the `APP_INITIALIZER` token.

</ngrx-docs-alert>

<ngrx-code-example header="main.ts">

```ts
import { bootstrapApplication } from '@angular/platform-browser';
import { provideStore } from '@ngrx/store';
import { provideEffects } from '@ngrx/effects';

import { AppComponent } from './app.component';
import { MoviesEffects } from './effects/movies.effects';
import * as actorsEffects from './effects/actors.effects';

bootstrapApplication(AppComponent, {
  providers: [
    provideStore(),
    provideEffects(MoviesEffects, actorsEffects),
  ],
});
```

</ngrx-code-example>

Feature-level effects are registered in the `providers` array of the route config.
The same `provideEffects()` method is used to register effects for a feature.

<ngrx-docs-alert type="inform">

Registering an effects class multiple times (for example in different lazy loaded features) does not cause the effects to run multiple times.

</ngrx-docs-alert>

<ngrx-code-example header="movie-routes.ts">

```ts
import { Route } from '@angular/router';
import { provideEffects } from '@ngrx/effects';

import { MoviesEffects } from './effects/movies.effects';
import * as actorsEffects from './effects/actors.effects';

export const routes: Route[] = [
  {
    path: 'movies',
    providers: [provideEffects(MoviesEffects, actorsEffects)],
  },
];
```

</ngrx-code-example>

### Alternative Way of Registering Effects

You can provide root-/feature-level effects with the provider `USER_PROVIDED_EFFECTS`.

<ngrx-code-example>

```ts
providers: [
  MoviesEffects,
  {
    provide: USER_PROVIDED_EFFECTS,
    multi: true,
    useValue: [MoviesEffects],
  },
];
```

</ngrx-code-example>

## Incorporating State

If additional metadata is needed to perform an effect besides the initiating action's `type`, we should rely on passed metadata from an action creator's `props` method.

Let's look at an example of an action initiating a login request using an effect with additional passed metadata:

<ngrx-code-example header="login-page.actions.ts">

```ts
import { createAction, props } from '@ngrx/store';
import { Credentials } from '../models/user';

export const login = createAction(
  '[Login Page] Login',
  props<{ credentials: Credentials }>()
);
```

</ngrx-code-example>

<ngrx-code-example header="auth.effects.ts">

```ts
import { Injectable, inject } from '@angular/core';
import { Actions, ofType, createEffect } from '@ngrx/effects';
import { of } from 'rxjs';
import { catchError, exhaustMap, map } from 'rxjs/operators';
import { LoginPageActions, AuthApiActions } from '../actions';
import { Credentials } from '../models/user';
import { AuthService } from '../services/auth.service';

@Injectable()
export class AuthEffects {
  private actions$ = inject(Actions);
  private authService = inject(AuthService);

  login$ = createEffect(() => {
    return this.actions$.pipe(
      ofType(LoginPageActions.login),
      exhaustMap((action) =>
        this.authService.login(action.credentials).pipe(
          map((user) => AuthApiActions.loginSuccess({ user })),
          catchError((error) =>
            of(AuthApiActions.loginFailure({ error }))
          )
        )
      )
    );
  });
}
```

</ngrx-code-example>

The `login` action has additional `credentials` metadata which is passed to a service to log the specific user into the application.

However, there may be cases when the required metadata is only accessible from state. When state is needed, the RxJS `withLatestFrom` or the @ngrx/effects `concatLatestFrom` operators can be used to provide it.

The example below shows the `addBookToCollectionSuccess$` effect displaying a different alert depending on the number of books in the collection state.

<ngrx-code-example header="collection.effects.ts">

```ts
import { Injectable, inject } from '@angular/core';
import { Store } from '@ngrx/store';
import {
  Actions,
  ofType,
  createEffect,
  concatLatestFrom,
} from '@ngrx/effects';
import { tap } from 'rxjs/operators';
import { CollectionApiActions } from '../actions';
import * as fromBooks from '../reducers';

@Injectable()
export class CollectionEffects {
  private actions$ = inject(Actions);
  private store = inject(Store<fromBooks.State>);

  addBookToCollectionSuccess$ = createEffect(
    () => {
      return this.actions$.pipe(
        ofType(CollectionApiActions.addBookSuccess),
        concatLatestFrom((_action) =>
          this.store.select(fromBooks.getCollectionBookIds)
        ),
        tap(([_action, bookCollection]) => {
          if (bookCollection.length === 1) {
            window.alert('Congrats on adding your first book!');
          } else {
            window.alert(
              'You have added book number ' + bookCollection.length
            );
          }
        })
      );
    },
    { dispatch: false }
  );
}
```

</ngrx-code-example>

<ngrx-docs-alert type="inform">

For performance reasons, use a flattening operator like `concatLatestFrom` to prevent the selector from firing until the correct action is dispatched.

</ngrx-docs-alert>

To learn about testing effects that incorporate state, see the [Effects that use State](guide/effects/testing#effect-that-uses-state) section in the testing guide.

## Using Other Observable Sources for Effects

Because effects are merely consumers of observables, they can be used without actions and the `ofType` operator. This is useful for effects that don't need to listen to some specific actions, but rather to some other observable source.

For example, imagine we want to track click events and send that data to our monitoring server. This can be done by creating an effect that listens to the `document` `click` event and emits the event data to our server.

<ngrx-code-example header="user-activity.effects.ts">

```ts
import { Injectable, inject } from '@angular/core';
import { Observable, fromEvent } from 'rxjs';
import { concatMap } from 'rxjs/operators';
import { createEffect } from '@ngrx/effects';

import { UserActivityService } from '../services/user-activity.service';

@Injectable()
export class UserActivityEffects {
  private userActivityService = inject(UserActivityService);

  trackUserActivity$ = createEffect(
    () => {
      return fromEvent(document, 'click').pipe(
        concatMap((event) =>
          this.userActivityService.trackUserActivity(event)
        )
      );
    },
    { dispatch: false }
  );
}
```

</ngrx-code-example>

<ngrx-docs-alert type="help">

An example of the `@ngrx/effects` in module-based applications is available at the [following link](https://v17.ngrx.io/guide/effects).

</ngrx-docs-alert>
