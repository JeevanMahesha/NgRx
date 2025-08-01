# Entity Management

The `@ngrx/signals/entities` plugin offers a simple and efficient way to manage entity collections with NgRx SignalStore.
This plugin provides the `withEntities` feature and a set of entity updaters.

## `withEntities` Feature

The `withEntities` feature integrates entity state into the store.
By default, `withEntities` requires an entity to have an `id` property, which serves as a unique identifier and must be of type `EntityId` (either a `string` or a `number`).

<ngrx-code-example header="todos-store.ts">

```ts
import { computed } from '@angular/core';
import { signalStore } from '@ngrx/signals';
import { withEntities } from '@ngrx/signals/entities';

type Todo = {
  id: number;
  text: string;
  completed: boolean;
};

export const TodosStore = signalStore(withEntities<Todo>());
```

</ngrx-code-example>

The `withEntities` feature adds the following signals to the `TodosStore`:

- `ids: Signal<EntityId[]>`: An array of all entity IDs.
- `entityMap: Signal<EntityMap<Todo>>`: A map of entities where each key is an ID.
- `entities: Signal<Todo[]>`: An array of all entities.

The `ids` and `entityMap` are state slices, while `entities` is a computed signal.

## Entity Updaters

The `entities` plugin provides a set of standalone entity updaters.
These functions can be used with `patchState` to facilitate entity collection updates.

<ngrx-code-example header="todos-store.ts">

```ts
import { patchState, signalStore, withMethods } from '@ngrx/signals';
import {
  addEntity,
  removeEntities,
  updateAllEntities,
  withEntities,
} from '@ngrx/signals/entities';

type Todo = {
  /* ... */
};

export const TodosStore = signalStore(
  withEntities<Todo>(),
  withMethods((store) => ({
    addTodo(todo: Todo): void {
      patchState(store, addEntity(todo));
    },
    removeEmptyTodos(): void {
      patchState(
        store,
        removeEntities(({ text }) => !text)
      );
    },
    completeAllTodos(): void {
      patchState(store, updateAllEntities({ completed: true }));
    },
  }))
);
```

</ngrx-code-example>

### `addEntity`

Adds an entity to the collection.
If the entity collection has an entity with the same ID, it is not overridden and no error is thrown.

```ts
patchState(store, addEntity(todo));
```

### `addEntities`

Adds multiple entities to the collection.
If the entity collection has entities with the same IDs, they are not overridden and no error is thrown.

```ts
patchState(store, addEntities([todo1, todo2]));
```

### `prependEntity`

Adds an entity to the beginning of the collection.
If the entity collection has an entity with the same ID, it is not added and no error is thrown.

```ts
patchState(store, prependEntity(todo));
```

### `prependEntities`

Adds multiple entities to the beginning of the collection, maintaining their relative order.
If the entity collection has entities with the same IDs, they are not added and no error is thrown.

```ts
patchState(store, prependEntities([todo1, todo2]));
```

### `updateEntity`

Updates an entity in the collection by ID. Supports partial updates. No error is thrown if an entity doesn't exist.

```ts
patchState(
  store,
  updateEntity({ id: 1, changes: { completed: true } })
);

patchState(
  store,
  updateEntity({
    id: 1,
    changes: (todo) => ({ completed: !todo.completed }),
  })
);
```

### `updateEntities`

Updates multiple entities in the collection by IDs or predicate. Supports partial updates. No error is thrown if entities don't exist.

```ts
// update entities by IDs
patchState(
  store,
  updateEntities({ ids: [1, 2], changes: { completed: true } })
);

patchState(
  store,
  updateEntities({
    ids: [1, 2],
    changes: (todo) => ({ completed: !todo.completed }),
  })
);

// update entities by predicate
patchState(
  store,
  updateEntities({
    predicate: ({ text }) => text.endsWith('✅'),
    changes: { text: '' },
  })
);

patchState(
  store,
  updateEntities({
    predicate: ({ text }) => text.endsWith('❓'),
    changes: (todo) => ({ text: todo.text.slice(0, -1) }),
  })
);
```

### `updateAllEntities`

Updates all entities in the collection. Supports partial updates. No error is thrown if entities don't exist.

```ts
patchState(store, updateAllEntities({ text: '' }));

patchState(
  store,
  updateAllEntities((todo) => ({ text: `${todo.text} ${todo.id}` }))
);
```

### `setEntity`

Adds or replaces an entity in the collection.

```ts
patchState(store, setEntity(todo));
```

### `setEntities`

Adds or replaces multiple entities in the collection.

```ts
patchState(store, setEntities([todo1, todo2]));
```

### `setAllEntities`

Replaces the current entity collection with the provided collection.

```ts
patchState(store, setAllEntities([todo1, todo2, todo3]));
```

### `upsertEntity`

Adds or updates an entity in the collection.
When updating, it does not replace the existing entity but merges it with the provided one.
Only the properties provided in the updated entity are merged with the existing entity.
Properties not present in the updated entity remain unchanged.

```ts
patchState(store, upsertEntity(todo));
```

### `upsertEntities`

Adds or updates multiple entities in the collection.
When updating, it does not replace existing entities but merges them with the provided ones.
Only the properties provided in updated entities are merged with existing entities.
Properties not present in updated entities remain unchanged.

```ts
patchState(store, upsertEntities([todo1, todo2]));
```

### `removeEntity`

Removes an entity from the collection by ID. No error is thrown if an entity doesn't exist.

```ts
patchState(store, removeEntity(1));
```

### `removeEntities`

Removes multiple entities from the collection by IDs or predicate. No error is thrown if entities don't exist.

```ts
// remove entities by IDs
patchState(store, removeEntities([1, 2]));

// remove entities by predicate
patchState(
  store,
  removeEntities((todo) => todo.completed)
);
```

### `removeAllEntities`

Removes all entities from the collection. No error is thrown if entities don't exist.

```ts
patchState(store, removeAllEntities());
```

## Custom Entity Identifier

If an entity doesn't have an identifier named `id`, a custom ID selector should be used.
The selector's return type should be either `string` or `number`.

Custom ID selectors should be provided when adding, setting, or updating entities.
Therefore, all variations of the `add*`, `set*`, and `update*` functions include an optional second argument, which is a config object that allows specifying the `selectId` function.

<ngrx-code-example header="todos-store.ts">

```ts
import { patchState, signalStore, withMethods } from '@ngrx/signals';
import {
  addEntities,
  removeEntity,
  SelectEntityId,
  setEntity,
  updateAllEntities,
  withEntities,
} from '@ngrx/signals/entities';

type Todo = {
  key: number;
  text: string;
  completed: boolean;
};

const selectId: SelectEntityId<Todo&gt = (todo) => todo.key;

export const TodosStore = signalStore(
  withEntities<Todo>(),
  withMethods((store) => ({
    addTodos(todos: Todo[]): void {
      patchState(store, addEntities(todos, { selectId }));
    },
    setTodo(todo: Todo): void {
      patchState(store, setEntity(todo, { selectId }));
    },
    completeAllTodos(): void {
      patchState(
        store,
        updateAllEntities({ completed: true }, { selectId })
      );
    },
    removeTodo(key: number): void {
      patchState(store, removeEntity(key));
    },
  }))
);
```

</ngrx-code-example>

The `remove*` updaters automatically select the correct identifier, so it is not necessary to provide a custom ID selector.

## Named Entity Collections

The `withEntities` feature allows specifying a custom prefix for entity properties by providing a collection name as an input argument.

<ngrx-code-example header="todos-store.ts">

```ts
import { signalStore, type } from '@ngrx/signals';
import { withEntities } from '@ngrx/signals/entities';

type Todo = {
  id: number;
  text: string;
  completed: boolean;
};

export const TodosStore = signalStore(
  // 💡 Entity type is specified using the `type` function.
  withEntities({ entity: type<Todo>(), collection: 'todo' })
);
```

</ngrx-code-example>

The names of the `TodosStore` properties are changed from `ids`, `entityMap`, and `entities` to `todoIds`, `todoEntityMap`, and `todoEntities`.

All updaters that operate on named entity collections require a collection name.

<ngrx-code-example header="todos-store.ts">

```ts
import {
  patchState,
  signalStore,
  type,
  withMethods,
} from '@ngrx/signals';
import {
  addEntity,
  removeEntity,
  withEntities,
} from '@ngrx/signals/entities';

type Todo = {
  /* ... */
};

export const TodosStore = signalStore(
  withEntities({ entity: type<Todo>(), collection: 'todo' }),
  withMethods((store) => ({
    addTodo(todo: Todo): void {
      patchState(store, addEntity(todo, { collection: 'todo' }));
    },
    removeTodo(id: number): void {
      patchState(store, removeEntity(id, { collection: 'todo' }));
    },
  }))
);
```

</ngrx-code-example>

<ngrx-docs-alert type="help">

Named entity collections allow managing multiple collections in a single store by using the `withEntities` feature multiple times.

```ts
export const LibraryStore = signalStore(
  withEntities({ entity: type<Book>(), collection: 'book' }),
  withEntities({ entity: type<Author>(), collection: 'author' }),
  withEntities({ entity: type<Category>(), collection: 'category' }),
  withMethods((store) => ({
    addBook(book: Book): void {
      patchState(store, addEntity(book, { collection: 'book' }));
    },
    addAuthor(author: Author): void {
      patchState(store, addEntity(author, { collection: 'author' }));
    },
    addCategory(category: Category): void {
      patchState(
        store,
        addEntity(category, { collection: 'category' })
      );
    },
  }))
);
```

Although it is possible to manage multiple collections in one store, in most cases, it is recommended to have dedicated stores for each entity type.

</ngrx-docs-alert>

## `entityConfig`

The `entityConfig` function reduces repetitive code when defining a custom entity configuration and ensures strong typing.
It accepts a config object where the entity type is required, and the collection name and custom ID selector are optional.

<ngrx-code-example header="todos-store.ts">

```ts
import {
  patchState,
  signalStore,
  type,
  withMethods,
} from '@ngrx/signals';
import {
  addEntity,
  entityConfig,
  removeEntity,
  withEntities,
} from '@ngrx/signals/entities';

type Todo = {
  key: number;
  text: string;
  completed: boolean;
};

const todoConfig = entityConfig({
  entity: type<Todo>(),
  collection: 'todo',
  selectId: (todo) => todo.key,
});

export const TodosStore = signalStore(
  withEntities(todoConfig),
  withMethods((store) => ({
    addTodo(todo: Todo): void {
      patchState(store, addEntity(todo, todoConfig));
    },
    removeTodo(todo: Todo): void {
      patchState(store, removeEntity(todo, todoConfig));
    },
  }))
);
```

</ngrx-code-example>

## Private Entity Collections

Private entity collections are defined by using the `_` prefix for the collection name.

```ts
const todoConfig = entityConfig({
  entity: type<Todo>(),
  // 👇 private collection
  collection: '_todo',
});

const TodosStore = signalStore(
  withEntities(todoConfig),
  withComputed(({ _todoEntities }) => ({
    // 👇 exposing entity array publicly
    todos: _todoEntities,
  }))
);

@Component({
  /* ... */
  template: `
    <h1>Todos</h1>
    <ngrx-todo-list [todos]="store.todos()" />
  `,
  providers: [TodosStore],
})
class Todos {
  readonly store = inject(TodosStore);
}
```

<ngrx-docs-alert type="help">

Learn more about private store members in the [Private Store Members](/guide/signals/signal-store/private-store-members) guide.

</ngrx-docs-alert>
