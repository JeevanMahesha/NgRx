<a name="20.0.0"></a>

# [20.0.0](https://github.com/ngrx/platform/compare/20.0.0-rc.0...20.0.0) (2025-07-28)

### Bug Fixes

- **www:** Make API Pages Responsive ([#4885](https://github.com/ngrx/platform/issues/4885)) ([7f09858](https://github.com/ngrx/platform/commit/7f09858)), closes [#4816](https://github.com/ngrx/platform/issues/4816)

<a name="20.0.0-rc.0"></a>

# [20.0.0-rc.0](https://github.com/ngrx/platform/compare/20.0.0-beta.0...20.0.0-rc.0) (2025-07-14)

### Bug Fixes

- **signals:** allow generic template literals as state keys ([#4871](https://github.com/ngrx/platform/issues/4871)) ([9fefc77](https://github.com/ngrx/platform/commit/9fefc77)), closes [#4638](https://github.com/ngrx/platform/issues/4638)
- **signals:** allow lazy initialization of DeepSignal ([#4866](https://github.com/ngrx/platform/issues/4866)) ([cb1a2ba](https://github.com/ngrx/platform/commit/cb1a2ba)), closes [#4749](https://github.com/ngrx/platform/issues/4749)
- **signals:** do not create deep signals for empty objects and unknown records with symbol keys ([#4880](https://github.com/ngrx/platform/issues/4880)) ([bae9f18](https://github.com/ngrx/platform/commit/bae9f18))
- **signals:** remove internal Signal type ([#4867](https://github.com/ngrx/platform/issues/4867)) ([4a4a5db](https://github.com/ngrx/platform/commit/4a4a5db))

### Features

- **operators:** add migration for deprecated tapResponse signature ([#4858](https://github.com/ngrx/platform/issues/4858)) ([551ceb4](https://github.com/ngrx/platform/commit/551ceb4))
- **signals:** add `withLinkedState()` ([#4818](https://github.com/ngrx/platform/issues/4818)) ([4bb7fdd](https://github.com/ngrx/platform/commit/4bb7fdd))
- **signals:** allow access to methods in `withComputed` ([#4864](https://github.com/ngrx/platform/issues/4864)) ([e11c23f](https://github.com/ngrx/platform/commit/e11c23f)), closes [#4846](https://github.com/ngrx/platform/issues/4846)
- **signals:** disallow user-defined signals in withState and signalState ([#4879](https://github.com/ngrx/platform/issues/4879)) ([306ed5a](https://github.com/ngrx/platform/commit/306ed5a))

<a name="20.0.0-beta.0"></a>

# [20.0.0-beta.0](https://github.com/ngrx/platform/compare/19.2.1...20.0.0-beta.0) (2025-06-30)

### Bug Fixes

- **signals:** handle events in the dispatched order ([#4857](https://github.com/ngrx/platform/issues/4857)) ([fa50f43](https://github.com/ngrx/platform/commit/fa50f43)), closes [#4852](https://github.com/ngrx/platform/issues/4852)
- **www:** Add padding to code snippets ([#4812](https://github.com/ngrx/platform/issues/4812)) ([9e942db](https://github.com/ngrx/platform/commit/9e942db)), closes [#4811](https://github.com/ngrx/platform/issues/4811)
- **www:** add styles for video ([#4851](https://github.com/ngrx/platform/issues/4851)) ([85680a0](https://github.com/ngrx/platform/commit/85680a0))
- **www:** fix color-scheme and combine duplicate html declarations ([#4855](https://github.com/ngrx/platform/issues/4855)) ([f9b2565](https://github.com/ngrx/platform/commit/f9b2565))
- **www:** remove duplicate scrollbar ([#4829](https://github.com/ngrx/platform/issues/4829)) ([f0f1f2a](https://github.com/ngrx/platform/commit/f0f1f2a)), closes [#4828](https://github.com/ngrx/platform/issues/4828)
- **www:** remove horizontal scrollbar ([#4808](https://github.com/ngrx/platform/issues/4808)) ([2639f67](https://github.com/ngrx/platform/commit/2639f67))

### build

- update to Angular 20 ([#4778](https://github.com/ngrx/platform/issues/4778)) ([8a4ecd9](https://github.com/ngrx/platform/commit/8a4ecd9))

### Features

- **effects:** remove act operator ([#4839](https://github.com/ngrx/platform/issues/4839)) ([9a83f1d](https://github.com/ngrx/platform/commit/9a83f1d))
- **entity:** strengthen typing of getInitialState ([#4819](https://github.com/ngrx/platform/issues/4819)) ([bfb21c2](https://github.com/ngrx/platform/commit/bfb21c2)), closes [#4422](https://github.com/ngrx/platform/issues/4422)
- **eslint-plugin:** add new rule enforce type call ([#4809](https://github.com/ngrx/platform/issues/4809)) ([9b82e67](https://github.com/ngrx/platform/commit/9b82e67)), closes [#4797](https://github.com/ngrx/platform/issues/4797)
- **operators:** deprecate `tapResponse` signature with a sequence of callbacks ([#4844](https://github.com/ngrx/platform/issues/4844)) ([9a16813](https://github.com/ngrx/platform/commit/9a16813)), closes [#4840](https://github.com/ngrx/platform/issues/4840)
- **signals:** allow user-defined signals in `withState` and `signalState` by splitting `STATE_SOURCE` ([#4795](https://github.com/ngrx/platform/issues/4795)) ([521a2a6](https://github.com/ngrx/platform/commit/521a2a6))
- **signals:** enhance `withComputed` to accept computation functions ([#4822](https://github.com/ngrx/platform/issues/4822)) ([c8b15dd](https://github.com/ngrx/platform/commit/c8b15dd)), closes [#4782](https://github.com/ngrx/platform/issues/4782)
- **www:** add sidebar for mobile view and make home page responsive ([#4813](https://github.com/ngrx/platform/issues/4813)) ([4397bfb](https://github.com/ngrx/platform/commit/4397bfb)), closes [#4807](https://github.com/ngrx/platform/issues/4807)

### BREAKING CHANGES

- **signals:** The internal `STATE_SOURCE` is no longer represented as a single `WritableSignal` holding the entire state object. Instead, each top-level state property becomes its own `WritableSignal` or remains as-is if a `WritableSignal` is provided as a state property.

BEFORE:

1. The initial state object reference is preserved:

const initialState = { ngrx: 'rocks' };

// signalState:
const state = signalState(initialState);
state() === initialState; // true

// withState:
const Store = signalStore(withState(initialState));
const store = new Store();
getState(store) === initialState; // true

2. Top-level `WritableSignal`s are wrapped with `Signal`s:

// signalState:
const state = signalState({ ngrx: signal('rocks') });
state.ngrx // type: Signal<WritableSignal<string>>

// withState:
const Store = signalStore(withState({ ngrx: signal('rocks') }));
const store = new Store();
store.ngrx // type: Signal<WritableSignal<string>>

3. Root state properties can be added dynamically:

// signalState:
const state = signalState<Record<string, string>>({});
console.log(state()); // {}

patchState(state, { ngrx: 'rocks' });
console.log(state()); // { ngrx: 'rocks' }

// withState:
const Store = signalStore(
{ protectedState: false },
withState<Record<string, string>>({})
);
const store = new Store();
console.log(getState(store)); // {}

patchState(store, { ngrx: 'rocks' });
console.log(getState(store)); // { ngrx: 'rocks' }

AFTER:

1. The initial state object reference is not preserved:

const initialState = { ngrx: 'rocks' };

// signalState:
const state = signalState(initialState);
state() === initialState; // false

// withState:
const Store = signalStore(withState(initialState));
const store = new Store();
getState(store) === initialState; // false

2. Top-level `WritableSignal`s are not wrapped with `Signal`s:

// signalState:
const state = signalState({ ngrx: signal('rocks') });
state.ngrx // type: Signal<string>

// withState:
const Store = signalStore(withState({ ngrx: signal('rocks') }));
const store = new Store();
store.ngrx // type: Signal<string>

3. Root state properties can not be added dynamically:

// signalState:
const state = signalState<Record<string, string>>({});
console.log(state()); // {}

patchState(state, { ngrx: 'rocks' });
console.log(state()); // {}

// withState:
const Store = signalStore(
{ protectedState: false },
withState<Record<string, string>>({})
);
const store = new Store();
console.log(getState(store)); // {}

patchState(store, { ngrx: 'rocks' });
console.log(getState(store)); // {}

Co-authored-by: Tim Deschryver <28659384+timdeschryver@users.noreply.github.com>
Co-authored-by: michael-small <33669563+michael-small@users.noreply.github.com>
Co-authored-by: Marko Stanimirović <markostanimirovic95@gmail.com>

- The minimum required version of Angular has been updated.

BEFORE:

The minimum required version is Angular 19.x

AFTER:

The minimum required version is Angular 20.x

<a name="20.0.0-beta.0"></a>

# [20.0.0-beta.0](https://github.com/ngrx/platform/compare/19.2.1...20.0.0-beta.0) (2025-06-10)

### Bug Fixes

- **www:** Add padding to code snippets ([#4812](https://github.com/ngrx/platform/issues/4812)) ([9e942db](https://github.com/ngrx/platform/commit/9e942db)), closes [#4811](https://github.com/ngrx/platform/issues/4811)
- **www:** remove horizontal scrollbar ([#4808](https://github.com/ngrx/platform/issues/4808)) ([2639f67](https://github.com/ngrx/platform/commit/2639f67))

### build

- update to Angular 20 ([#4778](https://github.com/ngrx/platform/issues/4778)) ([8a4ecd9](https://github.com/ngrx/platform/commit/8a4ecd9))

### Features

- **eslint-plugin:** add new rule enforce type call ([#4809](https://github.com/ngrx/platform/issues/4809)) ([9b82e67](https://github.com/ngrx/platform/commit/9b82e67)), closes [#4797](https://github.com/ngrx/platform/issues/4797)
- **www:** add sidebar for mobile view and make home page responsive ([#4813](https://github.com/ngrx/platform/issues/4813)) ([4397bfb](https://github.com/ngrx/platform/commit/4397bfb)), closes [#4807](https://github.com/ngrx/platform/issues/4807)

### BREAKING CHANGES

- The minimum required version of Angular has been updated.

BEFORE:

The minimum required version is Angular 19.x

AFTER:

The minimum required version is Angular 20.x

<a name="20.0.0"></a>

# [20.0.0](https://github.com/ngrx/platform/compare/19.2.1...20.0.0) (2025-06-09)

### Bug Fixes

- **www:** Add padding to code snippets ([#4812](https://github.com/ngrx/platform/issues/4812)) ([9e942db](https://github.com/ngrx/platform/commit/9e942db)), closes [#4811](https://github.com/ngrx/platform/issues/4811)
- **www:** remove horizontal scrollbar ([#4808](https://github.com/ngrx/platform/issues/4808)) ([2639f67](https://github.com/ngrx/platform/commit/2639f67))

### build

- update to Angular 20 ([#4778](https://github.com/ngrx/platform/issues/4778)) ([8a4ecd9](https://github.com/ngrx/platform/commit/8a4ecd9))

### Features

- **eslint-plugin:** add new rule enforce type call ([#4809](https://github.com/ngrx/platform/issues/4809)) ([9b82e67](https://github.com/ngrx/platform/commit/9b82e67)), closes [#4797](https://github.com/ngrx/platform/issues/4797)
- **www:** add sidebar for mobile view and make home page responsive ([#4813](https://github.com/ngrx/platform/issues/4813)) ([4397bfb](https://github.com/ngrx/platform/commit/4397bfb)), closes [#4807](https://github.com/ngrx/platform/issues/4807)

### BREAKING CHANGES

- The minimum required version of Angular has been updated.

BEFORE:

The minimum required version is Angular 19.x

AFTER:

The minimum required version is Angular 20.x

<a name="19.2.1"></a>

## [19.2.1](https://github.com/ngrx/platform/compare/19.2.0...19.2.1) (2025-05-29)

### Bug Fixes

- **signals:** add current state as second argument of case reducer ([#4800](https://github.com/ngrx/platform/issues/4800)) ([95dbbfa](https://github.com/ngrx/platform/commit/95dbbfa))
- **signals:** expose WritableStateSource to withFeature callback ([#4792](https://github.com/ngrx/platform/issues/4792)) ([afb6528](https://github.com/ngrx/platform/commit/afb6528)), closes [#4766](https://github.com/ngrx/platform/issues/4766)

<a name="19.2.0"></a>

# [19.2.0](https://github.com/ngrx/platform/compare/19.1.0...19.2.0) (2025-05-12)

### Features

- **eslint-plugin:** add schematic support for flat configs ([#4747](https://github.com/ngrx/platform/issues/4747)) ([f966d0a](https://github.com/ngrx/platform/commit/f966d0a))
- **signals:** add Events plugin ([#4769](https://github.com/ngrx/platform/issues/4769)) ([980cf6f](https://github.com/ngrx/platform/commit/980cf6f)), closes [#4580](https://github.com/ngrx/platform/issues/4580)

<a name="19.1.0"></a>

# [19.1.0](https://github.com/ngrx/platform/compare/19.0.1...19.1.0) (2025-04-01)

### Bug Fixes

- **signals:** skip assertions when ngDevMode is not defined ([#4703](https://github.com/ngrx/platform/issues/4703)) ([0b43014](https://github.com/ngrx/platform/commit/0b43014)), closes [#4699](https://github.com/ngrx/platform/issues/4699)

### Features

- **signals:** add `withFeature` ([#4739](https://github.com/ngrx/platform/issues/4739)) ([345ab4f](https://github.com/ngrx/platform/commit/345ab4f)), closes [#4678](https://github.com/ngrx/platform/issues/4678)
- **signals:** add prepend entity updaters ([#4721](https://github.com/ngrx/platform/issues/4721)) ([dac8665](https://github.com/ngrx/platform/commit/dac8665)), closes [#4723](https://github.com/ngrx/platform/issues/4723)
- **signals:** add RxMethod and SignalMethod types to public API ([#4744](https://github.com/ngrx/platform/issues/4744)) ([40e78d9](https://github.com/ngrx/platform/commit/40e78d9))
- **signals:** add unprotected testing helper ([#4725](https://github.com/ngrx/platform/issues/4725)) ([01c2327](https://github.com/ngrx/platform/commit/01c2327))
- **signals:** add upsert entity updaters ([#4727](https://github.com/ngrx/platform/issues/4727)) ([92fd7c3](https://github.com/ngrx/platform/commit/92fd7c3))
- **signals:** warn when reactive method runs with source injector ([#4742](https://github.com/ngrx/platform/issues/4742)) ([84a537c](https://github.com/ngrx/platform/commit/84a537c)), closes [#4726](https://github.com/ngrx/platform/issues/4726)

<a name="19.0.1"></a>

## [19.0.1](https://github.com/ngrx/platform/compare/19.0.0...19.0.1) (2025-01-31)

### Bug Fixes

- **signals:** enable `withProps` to handle Symbols ([#4656](https://github.com/ngrx/platform/issues/4656)) ([02320b3](https://github.com/ngrx/platform/commit/02320b3)), closes [#4655](https://github.com/ngrx/platform/issues/4655)
- **signals:** remove `signalMethod` instance watcher on destroy ([#4648](https://github.com/ngrx/platform/issues/4648)) ([7f42065](https://github.com/ngrx/platform/commit/7f42065)), closes [#4644](https://github.com/ngrx/platform/issues/4644)
- **signals:** revert the protection for state mutation in dev mode ([#4686](https://github.com/ngrx/platform/issues/4686)) ([ae7922e](https://github.com/ngrx/platform/commit/ae7922e)), closes [#4683](https://github.com/ngrx/platform/issues/4683)

<a name="19.0.0"></a>

# [19.0.0](https://github.com/ngrx/platform/compare/19.0.0-rc.0...19.0.0) (2024-12-17)

<a name="19.0.0-rc.0"></a>

# [19.0.0-rc.0](https://github.com/ngrx/platform/compare/19.0.0-beta.0...19.0.0-rc.0) (2024-12-10)

### Bug Fixes

- **eslint-plugin:** support ESM modudule syntax (.mjs) ([e2f35c8](https://github.com/ngrx/platform/commit/e2f35c8))
- **signals:** create deep signals for custom class instances ([#4614](https://github.com/ngrx/platform/issues/4614)) ([4d34dc4](https://github.com/ngrx/platform/commit/4d34dc4)), closes [#4604](https://github.com/ngrx/platform/issues/4604)

### Features

- **eslint-plugin:** add new rule require-super-ondestroy ([#4611](https://github.com/ngrx/platform/issues/4611)) ([2ac4372](https://github.com/ngrx/platform/commit/2ac4372)), closes [#4505](https://github.com/ngrx/platform/issues/4505)
- **signals:** add `signalMethod` ([#4597](https://github.com/ngrx/platform/issues/4597)) ([bdd1d3e](https://github.com/ngrx/platform/commit/bdd1d3e)), closes [#4581](https://github.com/ngrx/platform/issues/4581)
- **signals:** add `withProps` base feature ([#4607](https://github.com/ngrx/platform/issues/4607)) ([e626082](https://github.com/ngrx/platform/commit/e626082))
- **signals:** add migration for `withProps` ([#4612](https://github.com/ngrx/platform/issues/4612)) ([5f803d0](https://github.com/ngrx/platform/commit/5f803d0)), closes [#4608](https://github.com/ngrx/platform/issues/4608)
- **store:** enable dispatching actions on signal changes ([#4600](https://github.com/ngrx/platform/issues/4600)) ([2528d39](https://github.com/ngrx/platform/commit/2528d39)), closes [#4537](https://github.com/ngrx/platform/issues/4537)

### BREAKING CHANGES

- **signals:** - The `computed` property in `SignalStoreFeatureResult` type is renamed to `props`.

* The `EntityComputed` and `NamedEntityComputed` types in the `entities` plugin are renamed to `EntityProps` and `NamedEntityProps`.

BEFORE:

```ts
import { computed, Signal } from '@angular/core';
import {
  signalStoreFeature,
  SignalStoreFeature,
  type,
  withComputed,
} from '@ngrx/signals';
import { EntityComputed } from '@ngrx/signals/entities';

export function withTotalEntities<Entity>(): SignalStoreFeature<
  { state: {}; computed: EntityComputed<Entity>; methods: {} },
  { state: {}; computed: { total: Signal<number> }; methods: {} }
> {
  return signalStoreFeature(
    { computed: type<EntityComputed<Entity>>() },
    withComputed(({ entities }) => ({
      total: computed(() => entities().length),
    }))
  );
}
```

AFTER:

```ts
import { computed, Signal } from '@angular/core';
import {
  signalStoreFeature,
  SignalStoreFeature,
  type,
  withComputed,
} from '@ngrx/signals';
import { EntityProps } from '@ngrx/signals/entities';

export function withTotalEntities<Entity>(): SignalStoreFeature<
  { state: {}; props: EntityProps<Entity>; methods: {} },
  { state: {}; props: { total: Signal<number> }; methods: {} }
> {
  return signalStoreFeature(
    { props: type<EntityProps<Entity>>() },
    withComputed(({ entities }) => ({
      total: computed(() => entities().length),
    }))
  );
}
```

<a name="19.0.0-beta.0"></a>

# [19.0.0-beta.0](https://github.com/ngrx/platform/compare/18.1.1...19.0.0-beta.0") (2024-11-20)

### Features

- **schematics:** change standalone default to true for components ([#4569](https://github.com/ngrx/platform/issues/4569)) ([c7d0ce6](https://github.com/ngrx/platform/commit/c7d0ce6))
- **signals:** rename `rxMethod.unsubscribe` to `destroy` ([#4584](https://github.com/ngrx/platform/issues/4584)) ([57ad5c5](https://github.com/ngrx/platform/commit/57ad5c5))
- **signals:** throw error in dev mode on state mutation ([#4526](https://github.com/ngrx/platform/issues/4526)) ([7a84209](https://github.com/ngrx/platform/commit/7a84209))

### BREAKING CHANGES

- **signals:** The `signalState`/`signalStore` state object is frozen in development mode.
  If a mutable change occurs to the state object, an error will be thrown.

BEFORE:

```ts
const userState = signalState(initialState);
patchState(userState, (state) => {
  state.user.firstName = 'mutable change'; // mutable change which went through
  return state;
});
```

AFTER:

```ts
const userState = signalState(initialState);
patchState(userState, (state) => {
  state.user.firstName = 'mutable change'; // throws in dev mode
  return state;
});
```

- **signals:** The `unsubscribe` method from `rxMethod` is renamed to `destroy`.

BEFORE:

```ts
const logNumber = rxMethod<number>(tap(console.log));

const num1Ref = logNumber(interval(1_000));
const num2Ref = logNumber(interval(2_000));

// destroy `num1Ref` after 2 seconds
setTimeout(() => num1Ref.unsubscribe(), 2_000);

// destroy all reactive method refs after 5 seconds
setTimeout(() => logNumber.unsubscribe(), 5_000);
```

AFTER:

```ts
const logNumber = rxMethod<number>(tap(console.log));

const num1Ref = logNumber(interval(1_000));
const num2Ref = logNumber(interval(2_000));

// destroy `num1Ref` after 2 seconds
setTimeout(() => num1Ref.destroy(), 2_000);

// destroy all reactive method refs after 5 seconds
setTimeout(() => logNumber.destroy(), 5_000);
```

- **schematics:** The default setting for generating components using schematics is updated.

BEFORE:

The default setting for generating components using schematics does not use standalone components.

AFTER:

The default setting for generating components using schematics uses standalone components.

- The minimum required version of Angular has been updated.

BEFORE:

The minimum required version is Angular 18.x

AFTER:

The minimum required version is Angular 19.x

<a name="18.1.1"></a>

## [18.1.1](https://github.com/ngrx/platform/compare/18.1.0...18.1.1) (2024-10-29)

### Bug Fixes

- **data:** export HttpOptions ([#4564](https://github.com/ngrx/platform/issues/4564)) ([4909627](https://github.com/ngrx/platform/commit/4909627))
- **router-store:** use non-const enum to allow isolatedModules tsconfig option ([#4554](https://github.com/ngrx/platform/issues/4554)) ([f993759](https://github.com/ngrx/platform/commit/f993759))

<a name="18.1.0"></a>

# [18.1.0](https://github.com/ngrx/platform/compare/18.0.2...18.1.0) (2024-10-08)

### Bug Fixes

- **component-store:** remove [@ngrx](https://github.com/ngrx)/operators from dependencies ([#4532](https://github.com/ngrx/platform/issues/4532)) ([3b4b9c4](https://github.com/ngrx/platform/commit/3b4b9c4))
- **effects:** remove [@ngrx](https://github.com/ngrx)/operators from dependencies ([#4531](https://github.com/ngrx/platform/issues/4531)) ([4fb78f1](https://github.com/ngrx/platform/commit/4fb78f1))
- **signals:** remove usage of SIGNAL from [@angular](https://github.com/angular)/core/primitives/signals package ([#4530](https://github.com/ngrx/platform/issues/4530)) ([cae429a](https://github.com/ngrx/platform/commit/cae429a))
- **signals:** use `Injector` of `rxMethod` instance caller if available ([#4529](https://github.com/ngrx/platform/issues/4529)) ([ffc1d87](https://github.com/ngrx/platform/commit/ffc1d87)), closes [#4528](https://github.com/ngrx/platform/issues/4528)
- **store-devtools:** add [@angular](https://github.com/angular)/core as peer dependency ([#4478](https://github.com/ngrx/platform/issues/4478)) ([62cceeb](https://github.com/ngrx/platform/commit/62cceeb)), closes [#4479](https://github.com/ngrx/platform/issues/4479)

### Features

- **eslint-plugin:** add preferProtectedState rule ([#4488](https://github.com/ngrx/platform/issues/4488)) ([32c772d](https://github.com/ngrx/platform/commit/32c772d)), closes [#4474](https://github.com/ngrx/platform/issues/4474)
- **signals:** add deepComputed function ([#4539](https://github.com/ngrx/platform/issues/4539)) ([269bd32](https://github.com/ngrx/platform/commit/269bd32))

<a name="18.0.2"></a>

## [18.0.2](https://github.com/ngrx/platform/compare/18.0.1...18.0.2) (2024-07-31)

### Bug Fixes

- **eslint-plugin:** do not report non-array returns in no-multiple-actions-in-effects ([#4418](https://github.com/ngrx/platform/issues/4418)) ([92a68bc](https://github.com/ngrx/platform/commit/92a68bc))
- **operators:** add [@ngrx](https://github.com/ngrx)/operators to packageGroup for updates ([#4472](https://github.com/ngrx/platform/issues/4472)) ([521ce7b](https://github.com/ngrx/platform/commit/521ce7b)), closes [#4465](https://github.com/ngrx/platform/issues/4465)
- **signals:** allow modifying entity id on update ([#4404](https://github.com/ngrx/platform/issues/4404)) ([0106e93](https://github.com/ngrx/platform/commit/0106e93))

<a name="18.0.1"></a>

## [18.0.1](https://github.com/ngrx/platform/compare/18.0.0...18.0.1) (2024-06-27)

### Bug Fixes

- **component-store:** resolve issues in migration script to v18 ([#4403](https://github.com/ngrx/platform/issues/4403)) ([a15d53e](https://github.com/ngrx/platform/commit/a15d53e))
- **effects:** fix bugs in migration script to v18 ([#4402](https://github.com/ngrx/platform/issues/4402)) ([6ae4723](https://github.com/ngrx/platform/commit/6ae4723))
- **eslint-plugin:** only take return statement into account with no-multiple-actions-in-effects ([#4410](https://github.com/ngrx/platform/issues/4410)) ([c9c646c](https://github.com/ngrx/platform/commit/c9c646c)), closes [#4409](https://github.com/ngrx/platform/issues/4409)

### Features

- **signals:** rename signals to computed when defining custom features with input ([#4395](https://github.com/ngrx/platform/issues/4395)) ([05f0940](https://github.com/ngrx/platform/commit/05f0940)), closes [#4391](https://github.com/ngrx/platform/issues/4391)
- **signals:** replace `idKey` with `selectId` when defining custom entity ID ([#4396](https://github.com/ngrx/platform/issues/4396)) ([67a5a93](https://github.com/ngrx/platform/commit/67a5a93)), closes [#4217](https://github.com/ngrx/platform/issues/4217) [#4392](https://github.com/ngrx/platform/issues/4392)

<a name="18.0.1"></a>

## [18.0.1](https://github.com/ngrx/platform/compare/18.0.0...18.0.1) (2024-06-27)

<a name="18.0.0"></a>

# [18.0.0](https://github.com/ngrx/platform/compare/18.0.0-rc.1...18.0.0) (2024-06-13)

<a name="18.0.0-rc.1"></a>

# [18.0.0-rc.1](https://github.com/ngrx/platform/compare/18.0.0-rc.0...18.0.0-rc.1) (2024-06-12)

### Bug Fixes

- **eslint-plugin:** include signals to ESLint v8 rules ([#4387](https://github.com/ngrx/platform/issues/4387)) ([7c75dcf](https://github.com/ngrx/platform/commit/7c75dcf)), closes [#4385](https://github.com/ngrx/platform/issues/4385)

<a name="18.0.0-rc.0"></a>

# [18.0.0-rc.0](https://github.com/ngrx/platform/compare/18.0.0-beta.1...18.0.0-rc.0) (2024-06-10)

### Bug Fixes

- **router-store:** include string[] as return type for selectQueryParam ([#4369](https://github.com/ngrx/platform/issues/4369)) ([b0b43f7](https://github.com/ngrx/platform/commit/b0b43f7))
- **signals:** export DeepSignal ([#4377](https://github.com/ngrx/platform/issues/4377)) ([fa26c5c](https://github.com/ngrx/platform/commit/fa26c5c))

### Features

- **component-store:** remove tapResponse operator ([#4366](https://github.com/ngrx/platform/issues/4366)) ([285c810](https://github.com/ngrx/platform/commit/285c810))
- **effects:** remove concatLatestFrom operator ([#4367](https://github.com/ngrx/platform/issues/4367)) ([1a1b6df](https://github.com/ngrx/platform/commit/1a1b6df))
- **eslint-plugin:** add signals rules ([#4380](https://github.com/ngrx/platform/issues/4380)) ([c002466](https://github.com/ngrx/platform/commit/c002466))
- **eslint-plugin:** support ESLint v9 (and v8) ([#4371](https://github.com/ngrx/platform/issues/4371)) ([e8d9ffa](https://github.com/ngrx/platform/commit/e8d9ffa))

### BREAKING CHANGES

- **effects:** The concatLatestFrom operator has been removed from @ngrx/effects in favor of the @ngrx/operators package.

BEFORE:

import { concatLatestFrom } from '@ngrx/effects';

AFTER:

import { concatLatestFrom } from '@ngrx/operators';

- **component-store:** The tapResponse operator has been removed from @ngrx/component-store in favor of the @ngrx/operators package.

BEFORE:

import { tapResponse } from '@ngrx/component-store';

AFTER:

import { tapResponse } from '@ngrx/operators';

<a name="18.0.0-beta.1"></a>

# [18.0.0-beta.1](https://github.com/ngrx/platform/compare/18.0.0-beta.0...18.0.0-beta.1) (2024-05-20)

<a name="18.0.0-beta.0"></a>

# [18.0.0-beta.0](https://github.com/ngrx/platform/compare/17.2.0...18.0.0-beta.0) (2024-05-20)

### Bug Fixes

- **eslint-plugin:** add as devDependency via ng add ([#4343](https://github.com/ngrx/platform/issues/4343)) ([4fe7b7f](https://github.com/ngrx/platform/commit/4fe7b7f))
- **schematics:** set correct default value type ([#4307](https://github.com/ngrx/platform/issues/4307)) ([51034e6](https://github.com/ngrx/platform/commit/51034e6))

### Features

- **component-store:** add migrator for `tapResponse` ([#4321](https://github.com/ngrx/platform/issues/4321)) ([0ae21c9](https://github.com/ngrx/platform/commit/0ae21c9)), closes [#4261](https://github.com/ngrx/platform/issues/4261)
- **effects:** add migrator for `concatLatestFrom` ([#4311](https://github.com/ngrx/platform/issues/4311)) ([d264c56](https://github.com/ngrx/platform/commit/d264c56)), closes [#4262](https://github.com/ngrx/platform/issues/4262)
- **operators:** add `mapResponse` ([#4302](https://github.com/ngrx/platform/issues/4302)) ([c460920](https://github.com/ngrx/platform/commit/c460920)), closes [#4230](https://github.com/ngrx/platform/issues/4230)
- **store:** add TypedAction migration ([#4325](https://github.com/ngrx/platform/issues/4325)) ([f76a401](https://github.com/ngrx/platform/commit/f76a401))
- upgrade Angular dependencies to v18 pre-release versions ([#4308](https://github.com/ngrx/platform/issues/4308)) ([62f3971](https://github.com/ngrx/platform/commit/62f3971))
- **store:** merge Action and TypedAction intefaces ([#4318](https://github.com/ngrx/platform/issues/4318)) ([c8bde71](https://github.com/ngrx/platform/commit/c8bde71))

### BREAKING CHANGES

- The minimum required version of Angular has been updated

BEFORE:

The minimum required version of Angular is 17.x

AFTER:

The minimum required version of Angular is 18.x

- **store:** The Action and TypedAction interfaces are merged into one interface.

BEFORE:

There was a separation between the Action and TypedAction interfaces.

AFTER:

The Action interface accepts a generic type parameter that represents the payload type (defaults to string).
The TypedAction interface is removed.

<a name="17.2.0"></a>

# [17.2.0](https://github.com/ngrx/platform/compare/17.1.1...17.2.0) (2024-04-11)

### Bug Fixes

- **effects:** make createEffect work with TS 5.3 ([#4296](https://github.com/ngrx/platform/issues/4296)) ([19c1f11](https://github.com/ngrx/platform/commit/19c1f11))
- **ngrx.io:** set correct path for pwa icons ([#4263](https://github.com/ngrx/platform/issues/4263)) ([703a9c7](https://github.com/ngrx/platform/commit/703a9c7))
- **schematics:** correct module while generating a feature ([#4289](https://github.com/ngrx/platform/issues/4289)) ([7ecffe8](https://github.com/ngrx/platform/commit/7ecffe8)), closes [#4281](https://github.com/ngrx/platform/issues/4281)
- **signals:** make patchState work with TS 5.4 ([#4294](https://github.com/ngrx/platform/issues/4294)) ([6b440ee](https://github.com/ngrx/platform/commit/6b440ee))

### Features

- **component-store:** deprecate `tapResponse` export ([#4259](https://github.com/ngrx/platform/issues/4259)) ([a5958a0](https://github.com/ngrx/platform/commit/a5958a0))
- **effects:** deprecate `concatLatestFrom` export ([#4260](https://github.com/ngrx/platform/issues/4260)) ([79674b7](https://github.com/ngrx/platform/commit/79674b7))

<a name="17.1.1"></a>

## [17.1.1](https://github.com/ngrx/platform/compare/17.1.0...17.1.1) (2024-02-21)

### Bug Fixes

- **signals:** add `StateSignal` to the public API ([#4247](https://github.com/ngrx/platform/issues/4247)) ([3d45e5a](https://github.com/ngrx/platform/commit/3d45e5a))
- **signals:** correctly infer the type of methods with generics ([#4249](https://github.com/ngrx/platform/issues/4249)) ([70517ea](https://github.com/ngrx/platform/commit/70517ea))
- **signals:** run `rxMethod` outside of reactive context ([#4224](https://github.com/ngrx/platform/issues/4224)) ([3a691d9](https://github.com/ngrx/platform/commit/3a691d9))
- **store-devtools:** replace direct with indirect `eval` ([#4216](https://github.com/ngrx/platform/issues/4216)) ([1df0eb5](https://github.com/ngrx/platform/commit/1df0eb5)), closes [#4213](https://github.com/ngrx/platform/issues/4213)

### Performance Improvements

- **signals:** avoid creating unnecessary objects in excludeKeys ([#4240](https://github.com/ngrx/platform/issues/4240)) ([b90da9d](https://github.com/ngrx/platform/commit/b90da9d))
- **signals:** avoid unecessary observable conversions in rxMethod ([#4219](https://github.com/ngrx/platform/issues/4219)) ([fa45d92](https://github.com/ngrx/platform/commit/fa45d92))

<a name="17.1.0"></a>

# [17.1.0](https://github.com/ngrx/platform/compare/17.0.1...17.1.0) (2024-01-16)

### Bug Fixes

- **eslint-plugin:** only report main pipe violations ([#4169](https://github.com/ngrx/platform/issues/4169)) ([970514e](https://github.com/ngrx/platform/commit/970514e))
- **signals:** run `onDestroy` outside of injection context ([#4200](https://github.com/ngrx/platform/issues/4200)) ([e21df19](https://github.com/ngrx/platform/commit/e21df19))

### Features

- **signals:** add `withHooks` signature with factory input ([#4208](https://github.com/ngrx/platform/issues/4208)) ([916fba0](https://github.com/ngrx/platform/commit/916fba0)), closes [#4201](https://github.com/ngrx/platform/issues/4201)

<a name="17.0.1"></a>

## [17.0.1](https://github.com/ngrx/platform/compare/17.0.0...17.0.1) (2023-11-27)

### Bug Fixes

- **signals:** allow using signalStore and signalState in TS libs ([#4152](https://github.com/ngrx/platform/issues/4152)) ([ecc247c](https://github.com/ngrx/platform/commit/ecc247c))
- **signals:** define deep signals as configurable properties ([#4147](https://github.com/ngrx/platform/issues/4147)) ([890ca5b](https://github.com/ngrx/platform/commit/890ca5b))

<a name="17.0.0"></a>

# [17.0.0](https://github.com/ngrx/platform/compare/17.0.0-rc.0...17.0.0) (2023-11-20)

### Bug Fixes

- **data:** DefaultDataService getAll httpOptions fix + test ([#4134](https://github.com/ngrx/platform/issues/4134)) ([213e4c9](https://github.com/ngrx/platform/commit/213e4c9))
- **signals:** remove state checks for better DX ([#4124](https://github.com/ngrx/platform/issues/4124)) ([5749543](https://github.com/ngrx/platform/commit/5749543))

### Features

- **signals:** provide ability to use interface as state type ([#4133](https://github.com/ngrx/platform/issues/4133)) ([9c8304a](https://github.com/ngrx/platform/commit/9c8304a))

<a name="17.0.0-rc.0"></a>

# [17.0.0-rc.0](https://github.com/ngrx/platform/compare/17.0.0-beta.0...17.0.0-rc.0) (2023-11-10)

### Features

- **signals:** add `getState` function ([#4118](https://github.com/ngrx/platform/issues/4118)) ([79b0708](https://github.com/ngrx/platform/commit/79b0708))
- **signals:** add entities subpackage ([#4090](https://github.com/ngrx/platform/issues/4090)) ([f01bcd1](https://github.com/ngrx/platform/commit/f01bcd1))
- **store-devtools:** add migration for connectInZone ([#4106](https://github.com/ngrx/platform/issues/4106)) ([73fda59](https://github.com/ngrx/platform/commit/73fda59))
- **store-devtools:** change connectOutsideZone to be 'true' by default ([#4103](https://github.com/ngrx/platform/issues/4103)) ([d3b4db0](https://github.com/ngrx/platform/commit/d3b4db0)), closes [#4093](https://github.com/ngrx/platform/issues/4093)

<a name="17.0.0-beta.0"></a>

# [17.0.0-beta.0](https://github.com/ngrx/platform/compare/16.3.0...17.0.0-beta.0) (2023-10-30)

### Bug Fixes

- **entity:** set correct return type for getSelectors signature with parent selector ([#4074](https://github.com/ngrx/platform/issues/4074)) ([b3b571e](https://github.com/ngrx/platform/commit/b3b571e))
- **signals:** do not create nested signals for STATE_SIGNAL property ([#4062](https://github.com/ngrx/platform/issues/4062)) ([71a9d7f](https://github.com/ngrx/platform/commit/71a9d7f))
- **signals:** improve state type and add type tests ([#4064](https://github.com/ngrx/platform/issues/4064)) ([10c93ed](https://github.com/ngrx/platform/commit/10c93ed)), closes [#4065](https://github.com/ngrx/platform/issues/4065)

### Features

- **component:** remove `LetModule` ([#4087](https://github.com/ngrx/platform/issues/4087)) ([f28ea71](https://github.com/ngrx/platform/commit/f28ea71)), closes [#4077](https://github.com/ngrx/platform/issues/4077)
- **component:** remove PushModule ([7316d1a](https://github.com/ngrx/platform/commit/7316d1a))
- **effects:** deprecate act operator ([#4073](https://github.com/ngrx/platform/issues/4073)) ([3dbcadc](https://github.com/ngrx/platform/commit/3dbcadc))
- **operators:** introduce [@ngrx](https://github.com/ngrx)/operators package ([#4097](https://github.com/ngrx/platform/issues/4097)) ([e93ead4](https://github.com/ngrx/platform/commit/e93ead4)), closes [#4057](https://github.com/ngrx/platform/issues/4057)
- **signals:** remove selectSignal and rename withSignals to withComputed ([#4075](https://github.com/ngrx/platform/issues/4075)) ([25f95bc](https://github.com/ngrx/platform/commit/25f95bc))
- upgrade Angular dependencies to v17 pre-release versions ([#4068](https://github.com/ngrx/platform/issues/4068)) ([3d25047](https://github.com/ngrx/platform/commit/3d25047))
- **signals:** add rxjs-interop subpackage ([#4061](https://github.com/ngrx/platform/issues/4061)) ([fd565ed](https://github.com/ngrx/platform/commit/fd565ed))

### BREAKING CHANGES

- **component:** The LetModule is removed in favor of the standalone LetDirective.

BEFORE:

import { LetModule } from '@ngrx/component';

@NgModule({
imports: [
// ... other imports
LetModule,
],
})
export class MyFeatureModule {}

AFTER:

import { LetDirective } from '@ngrx/component';

@NgModule({
imports: [
// ... other imports
LetDirective,
],
})
export class MyFeatureModule {}

- **component:** The `PushModule` is deprecated in favor of the standalone `PushPipe`.

BEFORE:

```ts
import { PushModule } from '@ngrx/component';

@NgModule({
  imports: [
    // ... other imports
    PushModule,
  ],
})
export class MyFeatureModule {}
```

AFTER:

```ts
import { Component } from '@angular/core';
import { PushPipe } from '@ngrx/component';

@Component({
  // ... other metadata
  standalone: true,
  imports: [
    // ... other imports
    PushPipe,
  ],
})
export class MyStandaloneComponent {}
```

- **entity:** Selectors returned by the `adapter.getSelectors` signature that accepts a parent selector are strongly typed.

BEFORE:

```ts
const {
  selectIds, // type: (state: object) => string[] | number[]
  selectEntities, // type: (state: object) => Dictionary<Book>
  selectAll, // type: (state: object) => Book[]
  selectTotal, // type: (state: object) => number
} = adapter.getSelectors(selectBooksState);
```

AFTER:

```ts
const {
  selectIds, // type: MemoizedSelector<object, string[] | number[]>
  selectEntities, // type: MemoizedSelector<object, Dictionary<Book>>
  selectAll, // type: MemoizedSelector<object, Book[]>
  selectTotal, // type: MemoizedSelector<object, number>
} = adapter.getSelectors(selectBooksState);
```

- The minimum required version of Angular has been updated

BEFORE:

The minimum required version of Angular is 16.x

AFTER:

The minimum required version of Angular is 17.x

<a name="16.3.0"></a>

# [16.3.0](https://github.com/ngrx/platform/compare/16.2.0...16.3.0) (2023-10-03)

### Bug Fixes

- **schematics:** make action props plural ([#4017](https://github.com/ngrx/platform/issues/4017)) ([3a56412](https://github.com/ngrx/platform/commit/3a56412))

### Features

- **data:** standalone support for ng add [@ngrx](https://github.com/ngrx)/data ([#4019](https://github.com/ngrx/platform/issues/4019)) ([fdd701e](https://github.com/ngrx/platform/commit/fdd701e)), closes [#3935](https://github.com/ngrx/platform/issues/3935)
- **eslint-plugin:** add avoid-combining-component-store-selectors rule ([#4043](https://github.com/ngrx/platform/issues/4043)) ([0bff440](https://github.com/ngrx/platform/commit/0bff440))
- **eslint-plugin:** add new avoid-mapping-component-store-selectors rule ([#4026](https://github.com/ngrx/platform/issues/4026)) ([40477dd](https://github.com/ngrx/platform/commit/40477dd)), closes [#3940](https://github.com/ngrx/platform/issues/3940)
- **signals:** add `patchState` function and remove `$update` method ([#4037](https://github.com/ngrx/platform/issues/4037)) ([f2514ba](https://github.com/ngrx/platform/commit/f2514ba))
- **signals:** add signalState and selectSignal APIs ([#4007](https://github.com/ngrx/platform/issues/4007)) ([745d91f](https://github.com/ngrx/platform/commit/745d91f)), closes [#3993](https://github.com/ngrx/platform/issues/3993)
- **signals:** add signalStore and signalStoreFeature ([#4049](https://github.com/ngrx/platform/issues/4049)) ([0010281](https://github.com/ngrx/platform/commit/0010281)), closes [#4000](https://github.com/ngrx/platform/issues/4000)
- **signals:** initial setup ([#4002](https://github.com/ngrx/platform/issues/4002)) ([b0d63fd](https://github.com/ngrx/platform/commit/b0d63fd)), closes [#3992](https://github.com/ngrx/platform/issues/3992)
- **store:** prettify createFeature result ([#4014](https://github.com/ngrx/platform/issues/4014)) ([f179316](https://github.com/ngrx/platform/commit/f179316))

<a name="16.2.0"></a>

# [16.2.0](https://github.com/ngrx/platform/compare/16.1.0...16.2.0) (2023-08-07)

### Bug Fixes

- **data:** make DataServiceError extend from Error ([#3988](https://github.com/ngrx/platform/issues/3988)) ([0b98a65](https://github.com/ngrx/platform/commit/0b98a65))
- **effects:** register functional effects from object without prototype ([#3984](https://github.com/ngrx/platform/issues/3984)) ([1879cc9](https://github.com/ngrx/platform/commit/1879cc9)), closes [#3972](https://github.com/ngrx/platform/issues/3972)
- **eslint-plugin:** fix prefer-contact-latest-from rule to detect inject ([#3946](https://github.com/ngrx/platform/issues/3946)) ([2efd805](https://github.com/ngrx/platform/commit/2efd805))
- **eslint-plugin:** prefix-selectors-with-select suggestion ([#3959](https://github.com/ngrx/platform/issues/3959)) ([27f09df](https://github.com/ngrx/platform/commit/27f09df))
- **eslint-plugin:** support inject for no-typed-global-store rule ([#3951](https://github.com/ngrx/platform/issues/3951)) ([d3e84d8](https://github.com/ngrx/platform/commit/d3e84d8))
- **eslint-plugin:** support inject for use-consistent-global-store-name rule ([#3983](https://github.com/ngrx/platform/issues/3983)) ([caa74ff](https://github.com/ngrx/platform/commit/caa74ff))
- **store-devtools:** resolve memory leak when devtools are destroyed ([#3965](https://github.com/ngrx/platform/issues/3965)) ([644f0b6](https://github.com/ngrx/platform/commit/644f0b6))

### Features

- **eslint-plugin:** include docs URL in lint message ([#3944](https://github.com/ngrx/platform/issues/3944)) ([a1576de](https://github.com/ngrx/platform/commit/a1576de))
- **schematics:** add entity generation as part of feature schematic ([#3850](https://github.com/ngrx/platform/issues/3850)) ([19ebb0a](https://github.com/ngrx/platform/commit/19ebb0a))
- **store-devtools:** provide the ability to connect extension outside of Angular zone ([#3970](https://github.com/ngrx/platform/issues/3970)) ([1ee80e5](https://github.com/ngrx/platform/commit/1ee80e5)), closes [#3839](https://github.com/ngrx/platform/issues/3839)

<a name="16.1.0"></a>

# [16.1.0](https://github.com/ngrx/platform/compare/16.0.1...16.1.0) (2023-07-06)

### Bug Fixes

- **eslint:** fix inject function based injection not detecting store ([#3936](https://github.com/ngrx/platform/issues/3936)) ([8a5884d](https://github.com/ngrx/platform/commit/8a5884d)), closes [#3834](https://github.com/ngrx/platform/issues/3834)
- **eslint:** updater-explicit-return-type not applied when inheritance ([#3928](https://github.com/ngrx/platform/issues/3928)) ([41a5076](https://github.com/ngrx/platform/commit/41a5076))

### Features

- **component-store:** added custom equal option in select ([#3933](https://github.com/ngrx/platform/issues/3933)) ([c4b5cc5](https://github.com/ngrx/platform/commit/c4b5cc5))

<a name="16.0.1"></a>

## [16.0.1](https://github.com/ngrx/platform/compare/16.0.0...16.0.1) (2023-06-01)

### Bug Fixes

- **component:** untrack subscription in ngrxPush pipe ([#3918](https://github.com/ngrx/platform/issues/3918)) ([a1688e4](https://github.com/ngrx/platform/commit/a1688e4))
- **ngrx.io:** preserve sidenav width for larger menu items ([#3923](https://github.com/ngrx/platform/issues/3923)) ([ef73714](https://github.com/ngrx/platform/commit/ef73714))

<a name="16.0.0"></a>

# [16.0.0](https://github.com/ngrx/platform/compare/16.0.0-rc.0...16.0.0) (2023-05-09)

### Bug Fixes

- **component-store:** use default equality function for selectSignal ([#3884](https://github.com/ngrx/platform/issues/3884)) ([5843e7f](https://github.com/ngrx/platform/commit/5843e7f))
- **store:** add Signal equal function for immutable object comparison ([#3883](https://github.com/ngrx/platform/issues/3883)) ([634fdcb](https://github.com/ngrx/platform/commit/634fdcb))
- **store:** move Angular Signal interop into State service ([#3879](https://github.com/ngrx/platform/issues/3879)) ([8cb5795](https://github.com/ngrx/platform/commit/8cb5795)), closes [#3869](https://github.com/ngrx/platform/issues/3869)
- **store-devtools:** add state signal to StateObservable ([#3889](https://github.com/ngrx/platform/issues/3889)) ([ad6e14a](https://github.com/ngrx/platform/commit/ad6e14a))

### Features

- add ng add support for standalone config to NgRx packages ([#3881](https://github.com/ngrx/platform/issues/3881)) ([58508e3](https://github.com/ngrx/platform/commit/58508e3))
- **component:** add migration for LetModule and PushModule ([#3872](https://github.com/ngrx/platform/issues/3872)) ([5f07eda](https://github.com/ngrx/platform/commit/5f07eda))
- **component:** make LetDirective and PushPipe standalone ([#3826](https://github.com/ngrx/platform/issues/3826)) ([985d80c](https://github.com/ngrx/platform/commit/985d80c)), closes [#3804](https://github.com/ngrx/platform/issues/3804)
- **store:** add support of standalone API for ng add store ([#3874](https://github.com/ngrx/platform/issues/3874)) ([7aec84d](https://github.com/ngrx/platform/commit/7aec84d))

<a name="16.0.0-rc.1"></a>

# [16.0.0-rc.1](https://github.com/ngrx/platform/compare/16.0.0-rc.0...16.0.0-rc.1) (2023-05-09)

### Bug Fixes

- **component-store:** use default equality function for selectSignal ([#3884](https://github.com/ngrx/platform/issues/3884)) ([5843e7f](https://github.com/ngrx/platform/commit/5843e7f))
- **store:** add Signal equal function for immutable object comparison ([#3883](https://github.com/ngrx/platform/issues/3883)) ([634fdcb](https://github.com/ngrx/platform/commit/634fdcb))
- **store:** move Angular Signal interop into State service ([#3879](https://github.com/ngrx/platform/issues/3879)) ([8cb5795](https://github.com/ngrx/platform/commit/8cb5795)), closes [#3869](https://github.com/ngrx/platform/issues/3869)

### Features

- add ng add support for standalone config to NgRx packages ([#3881](https://github.com/ngrx/platform/issues/3881)) ([58508e3](https://github.com/ngrx/platform/commit/58508e3))
- **component:** add migration for LetModule and PushModule ([#3872](https://github.com/ngrx/platform/issues/3872)) ([5f07eda](https://github.com/ngrx/platform/commit/5f07eda))
- **component:** make LetDirective and PushPipe standalone ([#3826](https://github.com/ngrx/platform/issues/3826)) ([985d80c](https://github.com/ngrx/platform/commit/985d80c)), closes [#3804](https://github.com/ngrx/platform/issues/3804)
- **store:** add support of standalone API for ng add store ([#3874](https://github.com/ngrx/platform/issues/3874)) ([7aec84d](https://github.com/ngrx/platform/commit/7aec84d))

<a name="16.0.0-rc.0"></a>

# [16.0.0-rc.0](https://github.com/ngrx/platform/compare/16.0.0-beta.0...16.0.0-rc.0) (2023-05-04)

### Bug Fixes

- **data:** make non-optimistic add command entity partial ([#3859](https://github.com/ngrx/platform/issues/3859)) ([93ee1db](https://github.com/ngrx/platform/commit/93ee1db))

### Features

- **component-store:** add selectSignal options ([503e9d8](https://github.com/ngrx/platform/commit/503e9d8))
- **component-store:** add selectSignal signature that combines provided signals ([#3863](https://github.com/ngrx/platform/issues/3863)) ([07ba3fa](https://github.com/ngrx/platform/commit/07ba3fa))
- **store:** add selectSignal options ([0a13c4d](https://github.com/ngrx/platform/commit/0a13c4d))

<a name="16.0.0-beta.0"></a>

# [16.0.0-beta.0](https://github.com/ngrx/platform/compare/15.4.0...16.0.0-beta.0) (2023-04-27)

### Bug Fixes

- **data:** allow 0 to be a valid key ([#3830](https://github.com/ngrx/platform/issues/3830)) ([e50126d](https://github.com/ngrx/platform/commit/e50126d)), closes [#3828](https://github.com/ngrx/platform/issues/3828)
- **effects:** run user provided effects defined as injection token ([#3851](https://github.com/ngrx/platform/issues/3851)) ([cdaeeb6](https://github.com/ngrx/platform/commit/cdaeeb6)), closes [#3848](https://github.com/ngrx/platform/issues/3848)
- **store:** correctly infer action group events defined as empty object ([#3833](https://github.com/ngrx/platform/issues/3833)) ([dc78447](https://github.com/ngrx/platform/commit/dc78447))
- **store-devtools:** correctly import state when feature is set to true ([#3855](https://github.com/ngrx/platform/issues/3855)) ([0df3419](https://github.com/ngrx/platform/commit/0df3419)), closes [#3636](https://github.com/ngrx/platform/issues/3636)

### Features

- **component-store:** add selectSignal method for interop with Angular Signals ([#3861](https://github.com/ngrx/platform/issues/3861)) ([195d5ac](https://github.com/ngrx/platform/commit/195d5ac))
- **component-store:** add tapResponse signature with observer object ([#3829](https://github.com/ngrx/platform/issues/3829)) ([3a5e5d8](https://github.com/ngrx/platform/commit/3a5e5d8))
- **effects:** accept ObservableInput as concatLatestFrom argument ([#3838](https://github.com/ngrx/platform/issues/3838)) ([34dd28c](https://github.com/ngrx/platform/commit/34dd28c))
- **router-store:** add [@nrwl](https://github.com/nrwl)/angular data persistence operators ([#3841](https://github.com/ngrx/platform/issues/3841)) ([4482751](https://github.com/ngrx/platform/commit/4482751)), closes [#3777](https://github.com/ngrx/platform/issues/3777)
- **router-store:** remove deprecated getSelectors method ([#3816](https://github.com/ngrx/platform/issues/3816)) ([351a75e](https://github.com/ngrx/platform/commit/351a75e)), closes [#3815](https://github.com/ngrx/platform/issues/3815)
- **schematics:** replace `any` type with `unknown` type ([#3827](https://github.com/ngrx/platform/issues/3827)) ([0ea2933](https://github.com/ngrx/platform/commit/0ea2933))
- **schematics:** Use createActionGroup in schematics ([#3791](https://github.com/ngrx/platform/issues/3791)) ([f6ce20f](https://github.com/ngrx/platform/commit/f6ce20f))
- **store:** add createMockStore migration ([#3810](https://github.com/ngrx/platform/issues/3810)) ([ded4240](https://github.com/ngrx/platform/commit/ded4240))
- **store:** add selectSignal method for interop with Angular Signals ([#3856](https://github.com/ngrx/platform/issues/3856)) ([999dcb6](https://github.com/ngrx/platform/commit/999dcb6))
- **store:** preserve the event name case with createActionGroup ([#3832](https://github.com/ngrx/platform/issues/3832)) ([482fa5d](https://github.com/ngrx/platform/commit/482fa5d))
- **store:** remove deprecated createFeature method ([#3825](https://github.com/ngrx/platform/issues/3825)) ([fd8f347](https://github.com/ngrx/platform/commit/fd8f347)), closes [#3814](https://github.com/ngrx/platform/issues/3814)
- **store:** remove forbidden chars and empty str checks from createActionGroup ([#3857](https://github.com/ngrx/platform/issues/3857)) ([e37c57b](https://github.com/ngrx/platform/commit/e37c57b))
- convert entity and router selectors interfaces to types ([#3853](https://github.com/ngrx/platform/issues/3853)) ([73eb55c](https://github.com/ngrx/platform/commit/73eb55c))
- **store:** remove getMockStore in favor of createMockStore ([#3835](https://github.com/ngrx/platform/issues/3835)) ([8d0ed8e](https://github.com/ngrx/platform/commit/8d0ed8e))
- **store:** use strict projectors for createFeature selectors ([#3799](https://github.com/ngrx/platform/issues/3799)) ([bafd121](https://github.com/ngrx/platform/commit/bafd121))
- update to Angular v16.0.0-next.6 release ([#3831](https://github.com/ngrx/platform/issues/3831)) ([d7e03df](https://github.com/ngrx/platform/commit/d7e03df))

### BREAKING CHANGES

- **store:** The event name case is preserved when converting to the action name by using the `createActionGroup` function.

BEFORE:

All letters of the event name will be lowercase, except for the initial letters of words starting from the second word, which will be uppercase.

```ts
const authApiActions = createActionGroup({
  source: 'Auth API',
  events: {
    'LogIn Success': emptyProps(),
    'login failure': emptyProps(),
    'Logout Success': emptyProps(),
    logoutFailure: emptyProps(),
  },
});

// generated actions:
const { loginSuccess, loginFailure, logoutSuccess, logoutfailure } =
  authApiActions;
```

AFTER:

The initial letter of the first word of the event name will be lowercase, and the initial letters of the other words will be uppercase. The case of other letters in the event name will remain the same.

```ts
const { logInSuccess, loginFailure, logoutSuccess, logoutFailure } =
  authApiActions;
```

- **store:** The `createFeature` signature with root state is removed in favor of a signature without root state.
  An automatic migration is added to remove this signature.

BEFORE:

```ts
interface AppState {
  users: State;
}

export const usersFeature = createFeature<AppState>({
  name: 'users',
  reducer: createReducer(initialState /* case reducers */),
});
```

AFTER:

```ts
export const usersFeature = createFeature({
  name: 'users',
  reducer: createReducer(initialState /* case reducers */),
});
```

- **router-store:** The deprecated `getSelectors` function has been removed from the `@ngrx/router-store` package.

BEFORE:

The @ngrx/router-store package exports the `getSelectors` function.

AFTER:

The @ngrx/router-store package no longer exports the `getSelectors` function. A migration has been provided to replace existing usage

- **schematics:** NgRx Schematics do not use `any` types to define actions, these are replaced with the `unknown` type.

BEFORE:

Schematics used the `any` type to declare action payload type.

AFTER:

Schematics use the `unknown` type to declare action payload type.

- **store:** The `getMockStore` function is removed in favor of `createMockStore`

BEFORE:

```ts
import { getMockStore } from '@ngrx/store/testing';
const mockStore = getMockStore();
```

AFTER:

```ts
import { createMockStore } from '@ngrx/store/testing';
const mockStore = createMockStore();
```

- **store:** Projectors of selectors generated by createFeature are strongly typed.

BEFORE:

Projector function arguments of selectors generated by createFeature are not strongly typed:

```ts
const counterFeature = createFeature({
  name: 'counter',
  reducer: createReducer({ count: 0 }),
});

counterFeature.selectCount.projector;
// type: (...args: any[]) => number
```

AFTER:

Projector function arguments of selectors generated by createFeature are strongly typed:

```ts
const counterFeature = createFeature({
  name: 'counter',
  reducer: createReducer({ count: 0 }),
});

counterFeature.selectCount.projector;
// type: (featureState: { count: number; }) => number
```

<a name="15.4.0"></a>

# [15.4.0](https://github.com/ngrx/platform/compare/15.3.0...15.4.0) (2023-03-16)

### Bug Fixes

- **data:** correctly handle HttpOptions when provided ([#3795](https://github.com/ngrx/platform/issues/3795)) ([cbdf524](https://github.com/ngrx/platform/commit/cbdf524)), closes [#3794](https://github.com/ngrx/platform/issues/3794)
- **eslint-plugin:** ignore select name within createFeature ([#3788](https://github.com/ngrx/platform/issues/3788)) ([b58f9a3](https://github.com/ngrx/platform/commit/b58f9a3)), closes [#3786](https://github.com/ngrx/platform/issues/3786)

### Features

- **store:** rename getMockStore to createMockStore ([#3789](https://github.com/ngrx/platform/issues/3789)) ([6d615b3](https://github.com/ngrx/platform/commit/6d615b3)), closes [#3781](https://github.com/ngrx/platform/issues/3781)
- **store:** use createFeature in feature schematics ([#3776](https://github.com/ngrx/platform/issues/3776)) ([9b3647f](https://github.com/ngrx/platform/commit/9b3647f)), closes [#3741](https://github.com/ngrx/platform/issues/3741)

<a name="15.3.0"></a>

# [15.3.0](https://github.com/ngrx/platform/compare/15.2.1...15.3.0) (2023-02-13)

### Bug Fixes

- **store:** support using factory selectors as extra selectors ([#3767](https://github.com/ngrx/platform/issues/3767)) ([f4714c3](https://github.com/ngrx/platform/commit/f4714c3))

### Features

- **data:** Add HttpOptions to EntityActionOptions ([#3663](https://github.com/ngrx/platform/issues/3663)) ([#3664](https://github.com/ngrx/platform/issues/3664)) ([dd745c0](https://github.com/ngrx/platform/commit/dd745c0))

<a name="15.2.1"></a>

## [15.2.1](https://github.com/ngrx/platform/compare/15.2.0...15.2.1) (2023-01-26)

<a name="15.2.0"></a>

# [15.2.0](https://github.com/ngrx/platform/compare/15.1.0...15.2.0) (2023-01-26)

### Features

- **data:** add loadWithQuery method ([#3717](https://github.com/ngrx/platform/issues/3717)) ([06b97bf](https://github.com/ngrx/platform/commit/06b97bf)), closes [#3088](https://github.com/ngrx/platform/issues/3088)
- **effects:** add ability to create functional effects ([#3669](https://github.com/ngrx/platform/issues/3669)) ([dd76c63](https://github.com/ngrx/platform/commit/dd76c63)), closes [#3668](https://github.com/ngrx/platform/issues/3668)
- **router-store:** add migration for getRouterSelectors ([#3753](https://github.com/ngrx/platform/issues/3753)) ([a785331](https://github.com/ngrx/platform/commit/a785331))
- **router-store:** rename getSelectors to getRouterSelectors ([#3745](https://github.com/ngrx/platform/issues/3745)) ([7ad76b8](https://github.com/ngrx/platform/commit/7ad76b8)), closes [#3738](https://github.com/ngrx/platform/issues/3738)
- **store:** add ability to create extra selectors with createFeature ([#3744](https://github.com/ngrx/platform/issues/3744)) ([e4f873b](https://github.com/ngrx/platform/commit/e4f873b)), closes [#3719](https://github.com/ngrx/platform/issues/3719)
- **store:** add createFeature migration ([#3759](https://github.com/ngrx/platform/issues/3759)) ([b3c5931](https://github.com/ngrx/platform/commit/b3c5931))
- **store:** deprecate createFeature signature with root state ([#3756](https://github.com/ngrx/platform/issues/3756)) ([ccb3b93](https://github.com/ngrx/platform/commit/ccb3b93)), closes [#3737](https://github.com/ngrx/platform/issues/3737)

<a name="15.1.0"></a>

# [15.1.0](https://github.com/ngrx/platform/compare/15.0.0...15.1.0) (2022-12-21)

### Bug Fixes

- **component-store:** revert throwError usages with factory for RxJS 6 compatibility ([726dfb7](https://github.com/ngrx/platform/commit/726dfb7))
- **data:** revert throwError usages with factory for RxJS 6 compatibility ([a137b59](https://github.com/ngrx/platform/commit/a137b59)), closes [#3702](https://github.com/ngrx/platform/issues/3702)
- **eslint-plugin:** remove [@angular-devkit](https://github.com/angular-devkit)/schematics dependency ([#3710](https://github.com/ngrx/platform/issues/3710)) ([f0ae915](https://github.com/ngrx/platform/commit/f0ae915)), closes [#3709](https://github.com/ngrx/platform/issues/3709)
- **schematics:** disable package json peer dep updates during build ([#3692](https://github.com/ngrx/platform/issues/3692)) ([9cfc103](https://github.com/ngrx/platform/commit/9cfc103)), closes [#3691](https://github.com/ngrx/platform/issues/3691)
- **store:** support using `createActionGroup` with props typed as unions ([#3713](https://github.com/ngrx/platform/issues/3713)) ([e75fa1a](https://github.com/ngrx/platform/commit/e75fa1a)), closes [#3712](https://github.com/ngrx/platform/issues/3712)

### Features

- **router-store:** add new selectRouteDataParam selector ([#3673](https://github.com/ngrx/platform/issues/3673)) ([#3686](https://github.com/ngrx/platform/issues/3686)) ([81bc0d9](https://github.com/ngrx/platform/commit/81bc0d9))
- **store:** support using`createSelector` with selectors dictionary ([#3703](https://github.com/ngrx/platform/issues/3703)) ([5c87dda](https://github.com/ngrx/platform/commit/5c87dda)), closes [#3677](https://github.com/ngrx/platform/issues/3677)

<a name="15.0.0"></a>

# [15.0.0](https://github.com/ngrx/platform/compare/15.0.0-rc.0...15.0.0) (2022-11-29)

### Features

- **store-devtools:** add redux dev tool trace support ([#3517](https://github.com/ngrx/platform/issues/3517)) ([#3665](https://github.com/ngrx/platform/issues/3665)) ([187802a](https://github.com/ngrx/platform/commit/187802a)), closes [#1868](https://github.com/ngrx/platform/issues/1868)

<a name="15.0.0-rc.0"></a>

# [15.0.0-rc.0](https://github.com/ngrx/platform/compare/15.0.0-beta.1...15.0.0-rc.0) (2022-11-23)

### Features

- **component:** clear `LetDirective` view when replaced observable is in suspense state ([#3671](https://github.com/ngrx/platform/issues/3671)) ([ec59c4b](https://github.com/ngrx/platform/commit/ec59c4b))
- **component:** remove $ prefix from LetViewContext property names ([#3670](https://github.com/ngrx/platform/issues/3670)) ([b3b21e6](https://github.com/ngrx/platform/commit/b3b21e6))

### BREAKING CHANGES

- **component:** The `LetDirective` view will be cleared when the replaced observable is in a suspense state. Also, the `suspense` property is removed from the `LetViewContext` because it would always be `false` when the `LetDirective` view is rendered. Instead of `suspense` property, use the suspense template to handle the suspense state.

BEFORE:

The `LetDirective` view will not be cleared when the replaced observable is in a suspense state and the suspense template is not passed:

```ts
@Component({
  template: `
    <!-- When button is clicked, the 'LetDirective' view won't be cleared. -->
    <!-- Instead, the value of 'o' will be 'undefined' until the replaced -->
    <!-- observable emits the first value (after 1 second). -->
    <p *ngrxLet="obs$ as o">{{ o }}</p>
    <button (click)="replaceObs()">Replace Observable</button>
  `,
})
export class TestComponent {
  obs$ = of(1);

  replaceObs(): void {
    this.obs$ = of(2).pipe(delay(1000));
  }
}
```

AFTER:

The `LetDirective` view will be cleared when the replaced observable is in a suspense state and the suspense template is not passed:

```ts
@Component({
  template: `
    <!-- When button is clicked, the 'LetDirective' view will be cleared. -->
    <!-- The view will be created again when the replaced observable -->
    <!-- emits the first value (after 1 second). -->
    <p *ngrxLet="obs$ as o">{{ o }}</p>
    <button (click)="replaceObs()">Replace Observable</button>
  `,
})
export class TestComponent {
  obs$ = of(1);

  replaceObs(): void {
    this.obs$ = of(2).pipe(delay(1000));
  }
}
```

- **component:** The `$` prefix is removed from `LetViewContext` property names.

BEFORE:

```html
<ng-container *ngrxLet="obs$; $error as e; $complete as c">
  ...
</ng-container>
```

AFTER:

```html
<ng-container *ngrxLet="obs$; error as e; complete as c">
  ...
</ng-container>
```

<a name="15.0.0-beta.1"></a>

# [15.0.0-beta.1](https://github.com/ngrx/platform/compare/15.0.0-beta.0...15.0.0-beta.1) (2022-11-18)

### Features

- **data:** add initial standalone APIs ([#3647](https://github.com/ngrx/platform/issues/3647)) ([aa7ed66](https://github.com/ngrx/platform/commit/aa7ed66)), closes [#3553](https://github.com/ngrx/platform/issues/3553)
- **data:** add withEffects feature for provideEntityData ([#3656](https://github.com/ngrx/platform/issues/3656)) ([a6959e8](https://github.com/ngrx/platform/commit/a6959e8))
- **effects:** forRoot and forFeature accept spreaded array ([#3638](https://github.com/ngrx/platform/issues/3638)) ([0eaa536](https://github.com/ngrx/platform/commit/0eaa536))
- **router-store:** return resolved title via selectTitle ([#3648](https://github.com/ngrx/platform/issues/3648)) ([cc04e2f](https://github.com/ngrx/platform/commit/cc04e2f)), closes [#3622](https://github.com/ngrx/platform/issues/3622)
- **schematics:** add display block flag ([e0d368d](https://github.com/ngrx/platform/commit/e0d368d))
- **schematics:** add standalone flag ([b0bd2ff](https://github.com/ngrx/platform/commit/b0bd2ff))
- **schematics:** replace environments usage with isDevMode ([#3645](https://github.com/ngrx/platform/issues/3645)) ([4f61b63](https://github.com/ngrx/platform/commit/4f61b63)), closes [#3618](https://github.com/ngrx/platform/issues/3618)

### BREAKING CHANGES

- **router-store:** Property `title: string | undefined` is added to the `MinimalActivatedRouteSnapshot` interface.

BEFORE:

The `MinimalActivatedRouteSnapshot` interface doesn't contain the `title` property.

AFTER:

The `MinimalActivatedRouteSnapshot` interface contains the required `title` property.

<a name="15.0.0-beta.0"></a>

# [15.0.0-beta.0](https://github.com/ngrx/platform/compare/14.3.2...15.0.0-beta.0) (2022-11-03)

### Features

- **component:** add migration for replacing ReactiveComponentModule ([#3506](https://github.com/ngrx/platform/issues/3506)) ([49c6cf3](https://github.com/ngrx/platform/commit/49c6cf3)), closes [#3491](https://github.com/ngrx/platform/issues/3491)
- **component:** handle observable dictionaries ([#3602](https://github.com/ngrx/platform/issues/3602)) ([42efccb](https://github.com/ngrx/platform/commit/42efccb)), closes [#3545](https://github.com/ngrx/platform/issues/3545)
- **component:** remove ReactiveComponentModule ([#3643](https://github.com/ngrx/platform/issues/3643)) ([4bdf345](https://github.com/ngrx/platform/commit/4bdf345)), closes [#3623](https://github.com/ngrx/platform/issues/3623)
- **component-store:** Add SelectorObject to `select` ([#3629](https://github.com/ngrx/platform/issues/3629)) ([f8d0241](https://github.com/ngrx/platform/commit/f8d0241)), closes [#3632](https://github.com/ngrx/platform/issues/3632) [#3631](https://github.com/ngrx/platform/issues/3631)
- **effects:** change the signature of provideEffect ([#3587](https://github.com/ngrx/platform/issues/3587)) ([899afe7](https://github.com/ngrx/platform/commit/899afe7))
- **effects:** migration for provideEffects argument ([#3601](https://github.com/ngrx/platform/issues/3601)) ([f7dfeab](https://github.com/ngrx/platform/commit/f7dfeab))
- **effects:** remove @Effect decorator ([#3634](https://github.com/ngrx/platform/issues/3634)) ([96c5bdd](https://github.com/ngrx/platform/commit/96c5bdd)), closes [#3617](https://github.com/ngrx/platform/issues/3617)
- **eslint-plugin:** remove rules using @Effect ([#3635](https://github.com/ngrx/platform/issues/3635)) ([5f74e61](https://github.com/ngrx/platform/commit/5f74e61))
- **schematics:** drop support for TypeScript <4.8 ([#3631](https://github.com/ngrx/platform/issues/3631)) ([b9c1ab6](https://github.com/ngrx/platform/commit/b9c1ab6))
- **store:** make reducers arg of StoreModule.forRoot optional ([#3632](https://github.com/ngrx/platform/issues/3632)) ([e5177aa](https://github.com/ngrx/platform/commit/e5177aa))
- **store:** strict projector for selectors with props ([#3640](https://github.com/ngrx/platform/issues/3640)) ([351459f](https://github.com/ngrx/platform/commit/351459f)), closes [#3571](https://github.com/ngrx/platform/issues/3571)
- **store:** strict projectors ([#3581](https://github.com/ngrx/platform/issues/3581)) ([43198a2](https://github.com/ngrx/platform/commit/43198a2)), closes [#3571](https://github.com/ngrx/platform/issues/3571)

### BREAKING CHANGES

- **component:** `ReactiveComponentModule` is removed in favor of `LetModule` and `PushModule`.

BEFORE:

```ts
import { ReactiveComponentModule } from '@ngrx/component';

@NgModule({
  imports: [
    // ... other imports
    ReactiveComponentModule,
  ],
})
export class MyFeatureModule {}
```

AFTER:

```ts
import { LetModule, PushModule } from '@ngrx/component';

@NgModule({
  imports: [
    // ... other imports
    LetModule,
    PushModule,
  ],
})
export class MyFeatureModule {}
```

- **store:** The projector method has become strict

BEFORE:

You could pass any arguments to the projector method

const selector = createSelector(
selectString, // returning a string
selectNumber, // returning a number
(s, n, prefix: string) => {
return prefix + s.repeat(n);
}
)

// you could pass any argument
selector.projector(1, 'a', true);

AFTER:

const selector = createSelector(
selectString, // returning a string
selectNumber, // returning a number
(s, n, prefix: string) => {
return prefix + s.repeat(n);
}
)

// this throws
selector.projector(1, 'a', true);
// this does not throw because the arguments have the correct type
selector.projector(1, 'a', 'prefix');

- **store:** The projector function on the selector is type-safe by default.

BEFORE:

The projector is not type-safe by default, allowing for potential mismatch types in the projector function.

```ts
const mySelector = createSelector(
  () => 'one',
  () => 2,
  (one, two) => 3
);

mySelector.projector(); // <- type is projector(...args: any[]): number
```

AFTER:

The projector is strict by default, but can be bypassed with an `any` generic parameter.

```ts
const mySelector = createSelector(
  () => 'one',
  () => 2,
  (one, two) => 3
);

mySelector.projector(); // <- Results in type error. Type is projector(s1: string, s2: number): number
```

To retain previous behavior

```ts
const mySelector = createSelector(
  () => 'one',
  () => 2,
  (one, two) => 3
)(mySelector.projector as any)();
```

- **effects:** The @Effect decorator is removed

BEFORE:

Defining an effect is done with @Effect

@Effect()
data$ = this.actions$.pipe();

AFTER:

Defining an effect is done with createEffect

data$ = createEffect(() => this.actions$.pipe());

- **effects:** The signature of `provideEffects` is changed to expect a
  spreaded array of effects.

BEFORE:

`provideEffects` expecteded the effects to be passed as an array.

```ts
// single effect
provideEffects([MyEffect]);

// multiple effects
provideEffects([MyEffect, MySecondEffect]);
```

AFTER:

`provideEffects` expects the effects as a spreaded array as argument.

```ts
// single effect
provideEffects(MyEffect);

// multiple effects
provideEffects(MyEffect, MySecondEffect);
```

<a name="14.3.2"></a>

## [14.3.2](https://github.com/ngrx/platform/compare/14.3.1...14.3.2) (2022-10-04)

### Bug Fixes

- **component:** replace animationFrameScheduler with requestAnimationFrame ([#3592](https://github.com/ngrx/platform/issues/3592)) ([0a4d2dd](https://github.com/ngrx/platform/commit/0a4d2dd)), closes [#3591](https://github.com/ngrx/platform/issues/3591)
- **component-store:** use asapScheduler to schedule lifecycle hooks check ([#3580](https://github.com/ngrx/platform/issues/3580)) ([02431b4](https://github.com/ngrx/platform/commit/02431b4)), closes [#3573](https://github.com/ngrx/platform/issues/3573)
- **eslint-plugin:** avoid-combining-selectors with arrays should warn ([#3566](https://github.com/ngrx/platform/issues/3566)) ([4b0c6de](https://github.com/ngrx/platform/commit/4b0c6de))
- **router-store:** set undefined for unserializable route title ([#3593](https://github.com/ngrx/platform/issues/3593)) ([8eb4001](https://github.com/ngrx/platform/commit/8eb4001)), closes [#3495](https://github.com/ngrx/platform/issues/3495)
- **store:** fix typing of on fn ([#3577](https://github.com/ngrx/platform/issues/3577)) ([d054aa9](https://github.com/ngrx/platform/commit/d054aa9)), closes [#3576](https://github.com/ngrx/platform/issues/3576)

<a name="14.3.1"></a>

## [14.3.1](https://github.com/ngrx/platform/compare/14.3.0...14.3.1) (2022-09-08)

### Bug Fixes

- add support for TypeScript 4.8 ([#3548](https://github.com/ngrx/platform/issues/3548)) ([d558ce1](https://github.com/ngrx/platform/commit/d558ce1)), closes [#3547](https://github.com/ngrx/platform/issues/3547)
- **eslint-plugin:** avoid-mapping-selectors don't report on ThisExpression ([#3546](https://github.com/ngrx/platform/issues/3546)) ([a28175c](https://github.com/ngrx/platform/commit/a28175c)), closes [#3511](https://github.com/ngrx/platform/issues/3511)

<a name="14.3.0"></a>

# [14.3.0](https://github.com/ngrx/platform/compare/14.2.0...14.3.0) (2022-08-25)

### Features

- **effects:** add provideEffects function ([#3524](https://github.com/ngrx/platform/issues/3524)) ([db35bfe](https://github.com/ngrx/platform/commit/db35bfe)), closes [#3522](https://github.com/ngrx/platform/issues/3522)
- **router-store:** add provideRouterStore function ([#3532](https://github.com/ngrx/platform/issues/3532)) ([511b7cf](https://github.com/ngrx/platform/commit/511b7cf)), closes [#3528](https://github.com/ngrx/platform/issues/3528)
- **store:** add provideStore and provideState functions for standalone APIs ([#3539](https://github.com/ngrx/platform/issues/3539)) ([5639c1e](https://github.com/ngrx/platform/commit/5639c1e)), closes [#3526](https://github.com/ngrx/platform/issues/3526)
- **store-devtools:** add provideStoreDevtools function ([#3537](https://github.com/ngrx/platform/issues/3537)) ([6b0db4e](https://github.com/ngrx/platform/commit/6b0db4e)), closes [#3527](https://github.com/ngrx/platform/issues/3527)

<a name="14.2.0"></a>

# [14.2.0](https://github.com/ngrx/platform/compare/14.1.0...14.2.0) (2022-08-18)

### Bug Fixes

- **component-store:** make synchronous updater errors catchable ([#3490](https://github.com/ngrx/platform/issues/3490)) ([1a906fd](https://github.com/ngrx/platform/commit/1a906fd))
- **component-store:** move isInitialized check to queueScheduler context on state update ([#3492](https://github.com/ngrx/platform/issues/3492)) ([53636e4](https://github.com/ngrx/platform/commit/53636e4)), closes [#2991](https://github.com/ngrx/platform/issues/2991)

### Features

- **component-store:** handle errors in next callback ([#3533](https://github.com/ngrx/platform/issues/3533)) ([551c8eb](https://github.com/ngrx/platform/commit/551c8eb))

<a name="14.1.0"></a>

# [14.1.0](https://github.com/ngrx/platform/compare/14.0.2...14.1.0) (2022-08-09)

### Bug Fixes

- **eslint-plugin:** allow sequential dispatches in a different block context ([#3515](https://github.com/ngrx/platform/issues/3515)) ([faf446f](https://github.com/ngrx/platform/commit/faf446f)), closes [#3513](https://github.com/ngrx/platform/issues/3513)
- **eslint-plugin:** Remove the md suffix from the docsUrl path ([#3518](https://github.com/ngrx/platform/issues/3518)) ([71d4d4b](https://github.com/ngrx/platform/commit/71d4d4b))
- **store:** improve error for forbidden characters in createActionGroup ([#3496](https://github.com/ngrx/platform/issues/3496)) ([398fbed](https://github.com/ngrx/platform/commit/398fbed))

### Features

- **component:** add RenderScheduler to the public API ([#3516](https://github.com/ngrx/platform/issues/3516)) ([4642919](https://github.com/ngrx/platform/commit/4642919))
- **component:** replace markDirty with custom TickScheduler ([#3488](https://github.com/ngrx/platform/issues/3488)) ([3fcd8af](https://github.com/ngrx/platform/commit/3fcd8af))

### Performance Improvements

- **component:** do not schedule render for synchronous events ([#3487](https://github.com/ngrx/platform/issues/3487)) ([bb9071c](https://github.com/ngrx/platform/commit/bb9071c))

<a name="14.0.2"></a>

## [14.0.2](https://github.com/ngrx/platform/compare/14.0.1...14.0.2) (2022-07-12)

### Bug Fixes

- **component:** import operators from rxjs/operators ([#3479](https://github.com/ngrx/platform/issues/3479)) ([20ef7a4](https://github.com/ngrx/platform/commit/20ef7a4))
- **component-store:** effect handles generics that extend upon a type ([#3485](https://github.com/ngrx/platform/issues/3485)) ([9d2bda7](https://github.com/ngrx/platform/commit/9d2bda7)), closes [#3482](https://github.com/ngrx/platform/issues/3482)
- **data:** add TSDoc annotations ([#3483](https://github.com/ngrx/platform/issues/3483)) ([cbbc49f](https://github.com/ngrx/platform/commit/cbbc49f))
- **eslint-plugin:** fix configuration guide link ([#3480](https://github.com/ngrx/platform/issues/3480)) ([8219b1d](https://github.com/ngrx/platform/commit/8219b1d))

<a name="14.0.1"></a>

## [14.0.1](https://github.com/ngrx/platform/compare/14.0.0...14.0.1) (2022-06-29)

### Bug Fixes

- **component-store:** allow void callbacks in effect ([#3466](https://github.com/ngrx/platform/issues/3466)) ([e6dedd6](https://github.com/ngrx/platform/commit/e6dedd6)), closes [#3462](https://github.com/ngrx/platform/issues/3462)
- **component-store:** import operators from rxjs/operators ([#3465](https://github.com/ngrx/platform/issues/3465)) ([f9ba513](https://github.com/ngrx/platform/commit/f9ba513))
- **schematics:** add workingDirectory to schemas ([#3473](https://github.com/ngrx/platform/issues/3473)) ([50ea6b3](https://github.com/ngrx/platform/commit/50ea6b3)), closes [#3469](https://github.com/ngrx/platform/issues/3469)
- **schematics:** create schematicCollections if not exists ([#3470](https://github.com/ngrx/platform/issues/3470)) ([011cbcc](https://github.com/ngrx/platform/commit/011cbcc))

<a name="14.0.0"></a>

# [14.0.0](https://github.com/ngrx/platform/compare/14.0.0-rc.0...14.0.0) (2022-06-20)

### Bug Fixes

- **component:** do not exclude falsy types from LetDirective's input type ([#3460](https://github.com/ngrx/platform/issues/3460)) ([7028adb](https://github.com/ngrx/platform/commit/7028adb))

<a name="14.0.0-rc.0"></a>

# [14.0.0-rc.0](https://github.com/ngrx/platform/compare/14.0.0-beta.0...14.0.0-rc.0) (2022-06-08)

### Code Refactoring

- **router-store:** change name for full router state serializer ([#3430](https://github.com/ngrx/platform/issues/3430)) ([d443f50](https://github.com/ngrx/platform/commit/d443f50)), closes [#3416](https://github.com/ngrx/platform/issues/3416)

### Features

- **component:** add separate modules for PushPipe and LetDirective ([#3449](https://github.com/ngrx/platform/issues/3449)) ([eacc4b4](https://github.com/ngrx/platform/commit/eacc4b4)), closes [#3341](https://github.com/ngrx/platform/issues/3341)
- **component:** deprecate ReactiveComponentModule ([#3451](https://github.com/ngrx/platform/issues/3451)) ([b4dd2c8](https://github.com/ngrx/platform/commit/b4dd2c8))
- **eslint-plugin:** improve install flow ([#3447](https://github.com/ngrx/platform/issues/3447)) ([8ddaf60](https://github.com/ngrx/platform/commit/8ddaf60))
- **schematics:** use schematicCollections instead of defaultCollection ([#3441](https://github.com/ngrx/platform/issues/3441)) ([5abf828](https://github.com/ngrx/platform/commit/5abf828)), closes [#3383](https://github.com/ngrx/platform/issues/3383)

### BREAKING CHANGES

- **router-store:** The full router state serializer has been renamed.

BEFORE:

The full router state serializer is named `DefaultRouterStateSerializer`

AFTER:

The full router state serializer is named `FullRouterStateSerializer`. A migration is provided to rename the export in affected projects.

<a name="14.0.0-beta.0"></a>

# [14.0.0-beta.0](https://github.com/ngrx/platform/compare/13.1.0...14.0.0-beta.0) (2022-05-30)

- Closes #3344, #3345 ([70056a8](https://github.com/ngrx/platform/commit/70056a8)), closes [#3344](https://github.com/ngrx/platform/issues/3344) [#3345](https://github.com/ngrx/platform/issues/3345)

### Bug Fixes

- **store:** rename template literal to string literal for createActionGroup ([#3426](https://github.com/ngrx/platform/issues/3426)) ([7d08db1](https://github.com/ngrx/platform/commit/7d08db1))

### Features

- **schematics:** remove creators option ([#3311](https://github.com/ngrx/platform/issues/3311)) ([e86278a](https://github.com/ngrx/platform/commit/e86278a))
- update Angular packages to latest v14 RC ([#3425](https://github.com/ngrx/platform/issues/3425)) ([f15dd1e](https://github.com/ngrx/platform/commit/f15dd1e)), closes [#3417](https://github.com/ngrx/platform/issues/3417)
- **component:** add error as value to LetDirective's context ([#3380](https://github.com/ngrx/platform/issues/3380)) ([6452e24](https://github.com/ngrx/platform/commit/6452e24)), closes [#3343](https://github.com/ngrx/platform/issues/3343)
- **component:** add suspense template input to LetDirective ([#3377](https://github.com/ngrx/platform/issues/3377)) ([345ee53](https://github.com/ngrx/platform/commit/345ee53)), closes [#3340](https://github.com/ngrx/platform/issues/3340)
- **component:** use global render strategy in zone-less mode ([#3379](https://github.com/ngrx/platform/issues/3379)) ([f233dae](https://github.com/ngrx/platform/commit/f233dae)), closes [#3342](https://github.com/ngrx/platform/issues/3342)
- **component-store:** add OnStoreInit and OnStateInit lifecycle hooks ([#3368](https://github.com/ngrx/platform/issues/3368)) ([0ffed02](https://github.com/ngrx/platform/commit/0ffed02)), closes [#3335](https://github.com/ngrx/platform/issues/3335)
- **eslint-plugin:** add NgRx ESLint Plugin ([#3373](https://github.com/ngrx/platform/issues/3373)) ([ae0041b](https://github.com/ngrx/platform/commit/ae0041b))
- **store:** add createActionGroup function ([#3381](https://github.com/ngrx/platform/issues/3381)) ([2cdecb3](https://github.com/ngrx/platform/commit/2cdecb3)), closes [#3337](https://github.com/ngrx/platform/issues/3337)
- **store:** install and configure the [@ngrx](https://github.com/ngrx)/eslint-plugin on ng-add ([#3386](https://github.com/ngrx/platform/issues/3386)) ([bf2672e](https://github.com/ngrx/platform/commit/bf2672e))

### Performance Improvements

- **component:** reset state / trigger CD only if necessary ([#3328](https://github.com/ngrx/platform/issues/3328)) ([f5b055b](https://github.com/ngrx/platform/commit/f5b055b))

### BREAKING CHANGES

- 1. The context of `LetDirective` is strongly typed when `null` or
     `undefined` is passed as input.

BEFORE:

```html
<p *ngrxLet="null as n">{{ n }}</p>
<p *ngrxLet="undefined as u">{{ u }}</p>
```

- The type of `n` is `any`.
- The type of `u` is `any`.

AFTER:

```html
<p *ngrxLet="null as n">{{ n }}</p>
<p *ngrxLet="undefined as u">{{ u }}</p>
```

- The type of `n` is `null`.
- The type of `u` is `undefined`.

* **schematics:** BEFORE:

Creating actions, reducers, and effects is possible without using the creator syntax is possible.

AFTER:

- All schematics use the non-creator syntax to scaffold the code.
- The option `--creators` (and `-c`) is removed from the schematic options.
- The `skipTests` option is removed while generating actions.

* Minimum version of Angular has been updated

BEFORE:

Minimum version of Angular was 13.x

AFTER:

Minimum version of Angular is 14.x

- **component:** The native local rendering strategy is replaced by global
  in zone-less mode for better performance.

BEFORE:

The change detection is triggered via `changeDetectorRef.detectChanges`
in zone-less mode.

AFTER:

The change detection is triggered via `ɵmarkDirty` in zone-less mode.

- **component:** The `$error` property from `LetDirective`'s view context is
  a thrown error or `undefined` instead of `true`/`false`.

BEFORE:

```ts
<p *ngrxLet="obs$; $error as e">{{ e }}</p>
```

- `e` will be `true` when `obs$` emits error event.
- `e` will be `false` when `obs$` emits next/complete event.

AFTER:

```ts
<p *ngrxLet="obs$; $error as e">{{ e }}</p>
```

- `e` will be thrown error when `obs$` emits error event.
- `e` will be `undefined` when `obs$` emits next/complete event.

<a name="13.1.0"></a>

# [13.1.0](https://github.com/ngrx/platform/compare/13.0.2...13.1.0) (2022-03-28)

### Bug Fixes

- **component-store:** memoization not working when passing selectors directly to select ([#3356](https://github.com/ngrx/platform/issues/3356)) ([38bce88](https://github.com/ngrx/platform/commit/38bce88))
- **entity:** add default options to entity adapter when undefined is passed ([#3287](https://github.com/ngrx/platform/issues/3287)) ([17fe494](https://github.com/ngrx/platform/commit/17fe494))
- **store:** add explicit overloads for createSelector ([#3354](https://github.com/ngrx/platform/issues/3354)) ([2f82101](https://github.com/ngrx/platform/commit/2f82101)), closes [#3268](https://github.com/ngrx/platform/issues/3268)

### Features

- **data:** add ability to configure trailing slashes ([#3357](https://github.com/ngrx/platform/issues/3357)) ([56aedfd](https://github.com/ngrx/platform/commit/56aedfd))
- **store-devtools:** add REDUX_DEVTOOLS_EXTENSION injection token to public API ([#3338](https://github.com/ngrx/platform/issues/3338)) ([b55b0e4](https://github.com/ngrx/platform/commit/b55b0e4))

<a name="13.0.2"></a>

## [13.0.2](https://github.com/ngrx/platform/compare/13.0.1...13.0.2) (2021-12-07)

### Bug Fixes

- **component:** fixes recursive rendering ([#3255](https://github.com/ngrx/platform/issues/3255)) ([d24dde1](https://github.com/ngrx/platform/commit/d24dde1)), closes [#3246](https://github.com/ngrx/platform/issues/3246)
- **store:** remove afterEach hook in mock store ([#3245](https://github.com/ngrx/platform/issues/3245)) ([0640085](https://github.com/ngrx/platform/commit/0640085)), closes [#3243](https://github.com/ngrx/platform/issues/3243)
- **store:** update installation of the NgRx ESLint Plugin ([#3259](https://github.com/ngrx/platform/issues/3259)) ([df211fe](https://github.com/ngrx/platform/commit/df211fe))
- set correct dist paths for testing packages ([#3249](https://github.com/ngrx/platform/issues/3249)) ([ed9f6f1](https://github.com/ngrx/platform/commit/ed9f6f1)), closes [#3248](https://github.com/ngrx/platform/issues/3248)

<a name="13.0.1"></a>

## [13.0.1](https://github.com/ngrx/platform/compare/13.0.0...13.0.1) (2021-11-17)

### Bug Fixes

- **store:** add migration for create selector generics ([#3237](https://github.com/ngrx/platform/issues/3237)) ([5d97a11](https://github.com/ngrx/platform/commit/5d97a11))

<a name="13.0.0"></a>

# [13.0.0](https://github.com/ngrx/platform/compare/13.0.0-rc.0...13.0.0) (2021-11-16)

<a name="13.0.0-rc.0"></a>

# [13.0.0-rc.0](https://github.com/ngrx/platform/compare/13.0.0-beta.0...13.0.0-rc.0) (2021-11-11)

### Bug Fixes

- **data:** set loaded to true on queryManySuccess ([#3228](https://github.com/ngrx/platform/issues/3228)) ([52b828e](https://github.com/ngrx/platform/commit/52b828e)), closes [#3165](https://github.com/ngrx/platform/issues/3165)

### Features

- **store:** use variadic tuple types for createSelector ([#3023](https://github.com/ngrx/platform/issues/3023)) ([367d9b4](https://github.com/ngrx/platform/commit/367d9b4)), closes [#2715](https://github.com/ngrx/platform/issues/2715)
- update Angular packages to version 13.0.0 ([#3184](https://github.com/ngrx/platform/issues/3184)) ([996f1e8](https://github.com/ngrx/platform/commit/996f1e8)), closes [#3189](https://github.com/ngrx/platform/issues/3189)

### BREAKING CHANGES

- **store:** When manually specifying the generic arguments, you have to specify the selector's list of selector return values.

BEFORE:

```ts
createSelector<Story[], Story[], Story[][]>;
```

AFTER:

```ts
//        needs to be a tuple 👇
createSelector<Story[], [Story[]], Story[][]>;
```

- **data:** Now both the `getWithQuery` and `getAll` methods are consistent and do set `loaded` property to true on dispatching their success actions respectively.

BEFORE:

The `getWithQuery` method would not set the `loaded` property to true upon success

AFTER:

The `getWithQuery` method sets the `loaded` property to true upon success

<a name="13.0.0-beta.0"></a>

# [13.0.0-beta.0](https://github.com/ngrx/platform/compare/12.5.1...13.0.0-beta.0) (2021-11-04)

### Bug Fixes

- **component:** remove class-level generic from PushPipe ([#3127](https://github.com/ngrx/platform/issues/3127)) ([548c72c](https://github.com/ngrx/platform/commit/548c72c)), closes [#3114](https://github.com/ngrx/platform/issues/3114)
- **store:** infer initial store state properly with metareducers ([#3102](https://github.com/ngrx/platform/issues/3102)) ([d003b85](https://github.com/ngrx/platform/commit/d003b85)), closes [#3007](https://github.com/ngrx/platform/issues/3007)
- **store:** remove store config from forFeature signature with slice ([#3218](https://github.com/ngrx/platform/issues/3218)) ([b1a64dd](https://github.com/ngrx/platform/commit/b1a64dd)), closes [#3216](https://github.com/ngrx/platform/issues/3216)

### build

- build packages with Ivy ([#3219](https://github.com/ngrx/platform/issues/3219)) ([9e28050](https://github.com/ngrx/platform/commit/9e28050))

### Features

- **effects:** move createEffect migration to ng-update migration ([#3074](https://github.com/ngrx/platform/issues/3074)) ([5974913](https://github.com/ngrx/platform/commit/5974913))
- **store:** add createFeatureSelector migration ([#3214](https://github.com/ngrx/platform/issues/3214)) ([62334f9](https://github.com/ngrx/platform/commit/62334f9))
- **store:** provide better TS errors for action creator props ([#3060](https://github.com/ngrx/platform/issues/3060)) ([5ed3c3d](https://github.com/ngrx/platform/commit/5ed3c3d)), closes [#2892](https://github.com/ngrx/platform/issues/2892)

### BREAKING CHANGES

- The minimum version required for Angular and RxJS has been updated

BEFORE:

Angular 12.x is the minimum version
RxJS 6.5.x is the minimum required version

AFTER:

Angular 13.0.0-RC.0 is the minimum version
RxJS 7.4.x is the minimum required version

- **store:** The `StoreConfig` argument is removed from the `StoreModule.forFeature` signature with `FeatureSlice`.

BEFORE:

The `StoreModule.forFeature` signature with `FeatureSlice` has `StoreConfig` as the second input argument, but the configuration isn't registered if passed.

AFTER:

The `StoreModule.forFeature` signature with `FeatureSlice` no longer has `StoreConfig` as the second input argument.

- **store:** `initialState` needs to match the interface of the store/feature.

BEFORE:

Missing properties were valid

```ts
StoreModule.forRoot(reducers, {
  initialState: { notExisting: 3 },
  metaReducers: [metaReducer],
});
```

AFTER:

A type error is produced for initialState that does not match the store/feature

```ts
StoreModule.forRoot(reducers, {
  initialState: { notExisting: 3 },
  metaReducers: [metaReducer],
});
```

- **component:** PushPipe no longer has a class-level generic type parameter.

BEFORE:

Use of PushPipe outside of component templates required a generic

AFTER:

Use of PushPipe outside of component templates no longer requires a generic

- **store:** Types for props outside an action creator is more strictly checked

BEFORE:

Usage of `props` outside of an action creator with invalid types was allowed

AFTER:

Usage of `props` outside of an action creator now breaks for invalid types

- **effects:** The create-effect-migration migration is removed

BEFORE:

The Effect decorator removal and migration are done manually through schematics.

AFTER:

The Effect decorator removal and migration are performed automatically on upgrade to version 13 of NgRx Effects.

<a name="12.5.1"></a>

## [12.5.1](https://github.com/ngrx/platform/compare/12.5.0...12.5.1) (2021-10-25)

### Bug Fixes

- **router-store:** google upstream ([#3177](https://github.com/ngrx/platform/issues/3177)) ([20afb21](https://github.com/ngrx/platform/commit/20afb21))

<a name="12.5.0"></a>

# [12.5.0](https://github.com/ngrx/platform/compare/12.4.0...12.5.0) (2021-10-14)

### Bug Fixes

- **entity:** set correct input argument types for removeMutably methods ([#3148](https://github.com/ngrx/platform/issues/3148)) ([9611415](https://github.com/ngrx/platform/commit/9611415))
- **schematics:** add missing method ([#3157](https://github.com/ngrx/platform/issues/3157)) ([2a927a2](https://github.com/ngrx/platform/commit/2a927a2))
- **schematics:** use prefix option in feature schematic ([#3139](https://github.com/ngrx/platform/issues/3139)) ([5fa8890](https://github.com/ngrx/platform/commit/5fa8890)), closes [#3116](https://github.com/ngrx/platform/issues/3116)

### Features

- update to RxJS 7.4.x ([#3109](https://github.com/ngrx/platform/issues/3109)) ([4a42550](https://github.com/ngrx/platform/commit/4a42550))

<a name="12.4.0"></a>

# [12.4.0](https://github.com/ngrx/platform/compare/12.3.0...12.4.0) (2021-08-11)

### Bug Fixes

- **component:** capture errors from observable when using `ngrxPush` pipe and `ngrxLet` directive ([23c846b](https://github.com/ngrx/platform/commit/23c846b)), closes [#3100](https://github.com/ngrx/platform/issues/3100)

### Features

- **router-store:** add createRouterSelector to select router data for default config ([#3103](https://github.com/ngrx/platform/issues/3103)) ([507f58e](https://github.com/ngrx/platform/commit/507f58e))

<a name="12.3.0"></a>

# [12.3.0](https://github.com/ngrx/platform/compare/12.2.0...12.3.0) (2021-07-22)

### Bug Fixes

- **component-store:** accept error type in tapResponse with strict generic checks ([#3068](https://github.com/ngrx/platform/issues/3068)) ([3e02e37](https://github.com/ngrx/platform/commit/3e02e37)), closes [#3056](https://github.com/ngrx/platform/issues/3056)
- **data:** immutably delete an entity ([#3040](https://github.com/ngrx/platform/issues/3040)) ([a6c199f](https://github.com/ngrx/platform/commit/a6c199f)), closes [#2553](https://github.com/ngrx/platform/issues/2553)
- **data:** SAVE_ENTITIES_CANCELED type in SaveEntitiesCanceled ([#3079](https://github.com/ngrx/platform/issues/3079)) ([b24c1e0](https://github.com/ngrx/platform/commit/b24c1e0)), closes [#3065](https://github.com/ngrx/platform/issues/3065)
- **store:** make readonly usage consistent ([#3050](https://github.com/ngrx/platform/issues/3050)) ([#3069](https://github.com/ngrx/platform/issues/3069)) ([a39b278](https://github.com/ngrx/platform/commit/a39b278))

### Features

- **store:** make reducers accessible from ReducerManager ([#3064](https://github.com/ngrx/platform/issues/3064)) ([bf2bd1a](https://github.com/ngrx/platform/commit/bf2bd1a))

<a name="12.2.0"></a>

# [12.2.0](https://github.com/ngrx/platform/compare/12.1.0...12.2.0) (2021-06-29)

### Bug Fixes

- **component:** avoid early destruction of view in ngrxLet which interfered with animations ([#2890](https://github.com/ngrx/platform/issues/2890)) ([#3045](https://github.com/ngrx/platform/issues/3045)) ([7515e36](https://github.com/ngrx/platform/commit/7515e36))
- **data:** make options optional on add with partial ([#3043](https://github.com/ngrx/platform/issues/3043)) ([1620df9](https://github.com/ngrx/platform/commit/1620df9))

### Features

- **component-store:** accept error type in `tapResponse` ([#3056](https://github.com/ngrx/platform/issues/3056)) ([61e1963](https://github.com/ngrx/platform/commit/61e1963))

<a name="12.1.0"></a>

# [12.1.0](https://github.com/ngrx/platform/compare/12.0.0...12.1.0) (2021-06-09)

### Bug Fixes

- **data:** remove strict typing for optimistic false ([#3020](https://github.com/ngrx/platform/issues/3020)) ([3b565b4](https://github.com/ngrx/platform/commit/3b565b4)), closes [#2928](https://github.com/ngrx/platform/issues/2928)
- **store:** add ESLint plugin to TS overrides when possible ([#3032](https://github.com/ngrx/platform/issues/3032)) ([5102a34](https://github.com/ngrx/platform/commit/5102a34)), closes [#3031](https://github.com/ngrx/platform/issues/3031)

### Features

- **entity:** new `setMany` adapter ([#3026](https://github.com/ngrx/platform/issues/3026)) ([#3029](https://github.com/ngrx/platform/issues/3029)) ([a02ea9f](https://github.com/ngrx/platform/commit/a02ea9f))
- **schematics:** add the ability to create actions with the prefix ([#3025](https://github.com/ngrx/platform/issues/3025)) ([15bc0df](https://github.com/ngrx/platform/commit/15bc0df))
- **store:** add createFeature ([#3033](https://github.com/ngrx/platform/issues/3033)) ([5fd1c7b](https://github.com/ngrx/platform/commit/5fd1c7b)), closes [#2974](https://github.com/ngrx/platform/issues/2974)
- **store-devtools:** add autoPause option ([#2941](https://github.com/ngrx/platform/issues/2941)) ([698bd29](https://github.com/ngrx/platform/commit/698bd29)), closes [#2722](https://github.com/ngrx/platform/issues/2722)

<a name="12.0.0"></a>

# [12.0.0](https://github.com/ngrx/platform/compare/12.0.0-rc.0...12.0.0) (2021-05-12)

### Features

- **store:** register eslint-plugin-ngrx with ng add ([#3014](https://github.com/ngrx/platform/issues/3014)) ([5259890](https://github.com/ngrx/platform/commit/5259890))

<a name="12.0.0-rc.0"></a>

# [12.0.0-rc.0](https://github.com/ngrx/platform/compare/12.0.0-beta.1...12.0.0-rc.0) (2021-05-05)

<a name="12.0.0-beta.1"></a>

# [12.0.0-beta.1](https://github.com/ngrx/platform/compare/12.0.0-beta.0...12.0.0-beta.1) (2021-04-29)

### Bug Fixes

- **schematics:** assert empty as action observable ([#3005](https://github.com/ngrx/platform/issues/3005)) ([61b1ac7](https://github.com/ngrx/platform/commit/61b1ac7)), closes [#2931](https://github.com/ngrx/platform/issues/2931)

<a name="12.0.0-beta.0"></a>

# [12.0.0-beta.0](https://github.com/ngrx/platform/compare/11.1.1...12.0.0-beta.0) (2021-04-27)

### Bug Fixes

- **component:** include files in ng-add schematics ([ad13c9c](https://github.com/ngrx/platform/commit/ad13c9c))
- **component-store:** include files in ng-add schematics ([bfef622](https://github.com/ngrx/platform/commit/bfef622))
- **data:** include files in ng-add schematics ([526edd9](https://github.com/ngrx/platform/commit/526edd9))
- **effects:** ng-add schematics will generate effects files properly ([4389307](https://github.com/ngrx/platform/commit/4389307))
- **entity:** include files in ng-add schematics ([4d9f647](https://github.com/ngrx/platform/commit/4d9f647))
- **router-store:** include files in ng-add schematics ([eb71d5c](https://github.com/ngrx/platform/commit/eb71d5c))
- **store:** ng-add schematics will generate router files if minimal set to false ([74a2671](https://github.com/ngrx/platform/commit/74a2671))
- **store-devtools:** include files in ng-add schematics ([ac706de](https://github.com/ngrx/platform/commit/ac706de))

### build

- update to Angular libraries to version 12 RC.0 ([#3000](https://github.com/ngrx/platform/issues/3000)) ([4fb030e](https://github.com/ngrx/platform/commit/4fb030e))
- update to Nx version 12.0.x and TypeScript 4.1.x ([#2999](https://github.com/ngrx/platform/issues/2999)) ([cb258cb](https://github.com/ngrx/platform/commit/cb258cb))

### Features

- **store:** deprecate selectors with props ([#2993](https://github.com/ngrx/platform/issues/2993)) ([7c6d4e4](https://github.com/ngrx/platform/commit/7c6d4e4))

### BREAKING CHANGES

- Minimum versions of Angular and TypeScript have been updated

BEFORE:

Minimum of Angular version 11.x
Minimum of TypeScript 4.1.x

AFTER:

Minimum of Angular version 12.x
Minimum of TypeScript 4.2.x

- The minimum TypeScript version has been updated to 4.1.x

BEFORE:

The minimum TypeScript version is 4.0.x

AFTER:

The minimum TypeScript version is 4.1.x

<a name="11.1.1"></a>

## [11.1.1](https://github.com/ngrx/platform/compare/11.1.0...11.1.1) (2021-04-20)

### Bug Fixes

- **store:** adjust types to allow a generic reducer ([#2996](https://github.com/ngrx/platform/issues/2996)) ([7da57bc](https://github.com/ngrx/platform/commit/7da57bc)), closes [#2982](https://github.com/ngrx/platform/issues/2982)

### Features

- **store:** add FunctionWithParametersType to public API ([#2988](https://github.com/ngrx/platform/issues/2988)) ([fe7d058](https://github.com/ngrx/platform/commit/fe7d058)), closes [#2983](https://github.com/ngrx/platform/issues/2983)

<a name="11.1.0"></a>

# [11.1.0](https://github.com/ngrx/platform/compare/11.0.1...11.1.0) (2021-03-31)

### Bug Fixes

- **effects:** add support for Proxy objects in Effects ([#2976](https://github.com/ngrx/platform/issues/2976)) ([5f5b679](https://github.com/ngrx/platform/commit/5f5b679)), closes [#2975](https://github.com/ngrx/platform/issues/2975)
- **store:** allow default parameters in function action ([#2954](https://github.com/ngrx/platform/issues/2954)) ([9b23403](https://github.com/ngrx/platform/commit/9b23403)), closes [#2948](https://github.com/ngrx/platform/issues/2948)
- **store:** allow primitive types ([#2967](https://github.com/ngrx/platform/issues/2967)) ([eecc8ce](https://github.com/ngrx/platform/commit/eecc8ce)), closes [#2966](https://github.com/ngrx/platform/issues/2966)

### Features

- **component-store:** add ability for patchState to accept Observable ([#2937](https://github.com/ngrx/platform/issues/2937)) ([8930e22](https://github.com/ngrx/platform/commit/8930e22)), closes [#2852](https://github.com/ngrx/platform/issues/2852)
- **schematics:** add component store schematics ([#2886](https://github.com/ngrx/platform/issues/2886)) ([f086f80](https://github.com/ngrx/platform/commit/f086f80)), closes [#2570](https://github.com/ngrx/platform/issues/2570)

<a name="11.0.1"></a>

## [11.0.1](https://github.com/ngrx/platform/compare/11.0.0...11.0.1) (2021-02-15)

### Bug Fixes

- **schematics:** add index file ([#2923](https://github.com/ngrx/platform/issues/2923)) ([775c794](https://github.com/ngrx/platform/commit/775c794)), closes [#2917](https://github.com/ngrx/platform/issues/2917)
- **store:** forFeature using instanceof instead of typeof ([#2922](https://github.com/ngrx/platform/issues/2922)) ([2bea205](https://github.com/ngrx/platform/commit/2bea205)), closes [#2919](https://github.com/ngrx/platform/issues/2919)

<a name="11.0.0"></a>

# [11.0.0](https://github.com/ngrx/platform/compare/11.0.0-rc.0...11.0.0) (2021-02-09)

<a name="11.0.0-rc.0"></a>

# [11.0.0-rc.0](https://github.com/ngrx/platform/compare/11.0.0-beta.2...11.0.0-rc.0) (2021-02-04)

<a name="11.0.0-beta.2"></a>

# [11.0.0-beta.2](https://github.com/ngrx/platform/compare/11.0.0-beta.0...11.0.0-beta.2) (2021-02-02)

### Bug Fixes

- **component:** remove ? from LetViewContext props to prevent 'possibly undefined' error in strict mode ([#2876](https://github.com/ngrx/platform/issues/2876)) ([c3ac252](https://github.com/ngrx/platform/commit/c3ac252))
- **component:** transform to Observable if Input is Promise ([b611367](https://github.com/ngrx/platform/commit/b611367))
- **data:** make entity param partial when is not optimistic ([#2899](https://github.com/ngrx/platform/issues/2899)) ([bb70e6c](https://github.com/ngrx/platform/commit/bb70e6c)), closes [#2870](https://github.com/ngrx/platform/issues/2870)
- **data:** type overloaded add for is optimistic true | undefined ([#2906](https://github.com/ngrx/platform/issues/2906)) ([6d46ac4](https://github.com/ngrx/platform/commit/6d46ac4))
- **push:** fix return typing for observables to include undefined ([#2907](https://github.com/ngrx/platform/issues/2907)) ([abcc599](https://github.com/ngrx/platform/commit/abcc599)), closes [#2888](https://github.com/ngrx/platform/issues/2888)
- **router-store:** cast return type as RouterReducerState ([#2887](https://github.com/ngrx/platform/issues/2887)) ([d489484](https://github.com/ngrx/platform/commit/d489484))

### Features

- **effects:** concatLatestFrom operator ([#2760](https://github.com/ngrx/platform/issues/2760)) ([55f0f7a](https://github.com/ngrx/platform/commit/55f0f7a))
- **effects:** deprecate @Effect decorator ([#2855](https://github.com/ngrx/platform/issues/2855)) ([dbd1ecf](https://github.com/ngrx/platform/commit/dbd1ecf))
- **store:** add object-style StoreModule.forFeature overload w/fixes ([#2885](https://github.com/ngrx/platform/issues/2885)) ([a9468e1](https://github.com/ngrx/platform/commit/a9468e1)), closes [#2821](https://github.com/ngrx/platform/issues/2821) [#2809](https://github.com/ngrx/platform/issues/2809)
- **store-devtools:** pass entire error object to the error handler ([#2853](https://github.com/ngrx/platform/issues/2853)) ([ce28b44](https://github.com/ngrx/platform/commit/ce28b44)), closes [#2824](https://github.com/ngrx/platform/issues/2824)

### Performance Improvements

- **schematics:** speed up create effect migration ([#2873](https://github.com/ngrx/platform/issues/2873)) ([2f5dcb4](https://github.com/ngrx/platform/commit/2f5dcb4))

### BREAKING CHANGES

- **push:** BEFORE:

ngrxPush typing doesn't consider `undefined` when the input type is an observable

AFTER:

ngrxPush typing considers `undefined` when the input type is an observable

<a name="11.0.0-beta.0"></a>

# [11.0.0-beta.0](https://github.com/ngrx/platform/compare/10.0.1...11.0.0-beta.0) (2021-01-05)

### Bug Fixes

- update Angular peer dependencies to version 11 ([#2843](https://github.com/ngrx/platform/issues/2843)) ([f63d281](https://github.com/ngrx/platform/commit/f63d281)), closes [#2842](https://github.com/ngrx/platform/issues/2842)
- **component:** add schematic assets to ng-package.json ([9598527](https://github.com/ngrx/platform/commit/9598527)), closes [#2819](https://github.com/ngrx/platform/issues/2819)
- **component-store:** add schematic assets to ng-package.json ([0e3b52d](https://github.com/ngrx/platform/commit/0e3b52d)), closes [#2819](https://github.com/ngrx/platform/issues/2819)
- **component-store:** adjust updater to accept partials ([#2765](https://github.com/ngrx/platform/issues/2765)) ([b54b9b6](https://github.com/ngrx/platform/commit/b54b9b6)), closes [#2754](https://github.com/ngrx/platform/issues/2754)
- **router-store:** ingore slash when comparing routes ([#2834](https://github.com/ngrx/platform/issues/2834)) ([cad3f60](https://github.com/ngrx/platform/commit/cad3f60)), closes [#2829](https://github.com/ngrx/platform/issues/2829) [#1781](https://github.com/ngrx/platform/issues/1781)
- **schematics:** add schematics to devDependencies ([#2784](https://github.com/ngrx/platform/issues/2784)) ([daf1889](https://github.com/ngrx/platform/commit/daf1889))
- **store:** add noop for all methods in MockReducerManager ([#2777](https://github.com/ngrx/platform/issues/2777)) ([a489b48](https://github.com/ngrx/platform/commit/a489b48)), closes [#2776](https://github.com/ngrx/platform/issues/2776)
- **store:** correct types for SelectorFactoryConfig ([#2752](https://github.com/ngrx/platform/issues/2752)) ([aa9bf1a](https://github.com/ngrx/platform/commit/aa9bf1a))

### Code Refactoring

- use consistent naming of injection tokens across packages ([#2737](https://github.com/ngrx/platform/issues/2737)) ([e02d0d4](https://github.com/ngrx/platform/commit/e02d0d4))

### Features

- **component-store:** add patchState method ([#2788](https://github.com/ngrx/platform/issues/2788)) ([ecedadb](https://github.com/ngrx/platform/commit/ecedadb))
- **component-store:** add tapResponse operator ([#2763](https://github.com/ngrx/platform/issues/2763)) ([d1873c9](https://github.com/ngrx/platform/commit/d1873c9))
- **component-store:** allow more than 4 selects ([#2841](https://github.com/ngrx/platform/issues/2841)) ([7c29320](https://github.com/ngrx/platform/commit/7c29320))
- **effects:** add support for provideMockActions outside of the TestBed ([#2762](https://github.com/ngrx/platform/issues/2762)) ([c47114c](https://github.com/ngrx/platform/commit/c47114c))
- **effects:** allow usage of empty forRoot array multiple times ([#2774](https://github.com/ngrx/platform/issues/2774)) ([5219ff5](https://github.com/ngrx/platform/commit/5219ff5))
- **entity:** remove addAll ([#2783](https://github.com/ngrx/platform/issues/2783)) ([93a4754](https://github.com/ngrx/platform/commit/93a4754))
- **router-store:** add selectParamFromRouterState selector ([#2771](https://github.com/ngrx/platform/issues/2771)) ([3a1f359](https://github.com/ngrx/platform/commit/3a1f359)), closes [#2758](https://github.com/ngrx/platform/issues/2758)
- **router-store:** Add urlAfterRedirects ([#2775](https://github.com/ngrx/platform/issues/2775)) ([14553f6](https://github.com/ngrx/platform/commit/14553f6))
- **store:** add object-style StoreModule.forFeature overload ([#2821](https://github.com/ngrx/platform/issues/2821)) ([17571e5](https://github.com/ngrx/platform/commit/17571e5)), closes [#2809](https://github.com/ngrx/platform/issues/2809)
- **store:** add support for provideMockStore outside of the TestBed ([#2759](https://github.com/ngrx/platform/issues/2759)) ([1650582](https://github.com/ngrx/platform/commit/1650582)), closes [#2745](https://github.com/ngrx/platform/issues/2745)

### Performance Improvements

- **router-store:** optimize selectQueryParams, selectQueryParam and selectFragment selectors ([#2764](https://github.com/ngrx/platform/issues/2764)) ([918f184](https://github.com/ngrx/platform/commit/918f184))

### BREAKING CHANGES

- **router-store:** Router-store selectors for query params and fragment select from the root router state node. This could potentially break unit tests, but is functionally equivalent to the current behavior at runtime.

BEFORE:

selectQueryParams - returns query params from the last router state node
selectQueryParam - returns a query param from the last router state node
selectFragment - returns the fragment from the last router state node

AFTER:

selectQueryParams - returns query params from routerState.root
selectQueryParam - returns a query param from routerState.root
selectFragment - returns the fragment from routerState.root

- Angular peer dependency versions are bumped to latest major (11)

BEFORE:

Minimum Angular peer dependency version is ^10.0.0

AFTER:

Minimum Angular peer dependency version is ^11.0.0

- **entity:** To overwrite the entities, we previously used the `addAll` method but the method name was confusing.

BEFORE:

```ts
adapter.addAll(action.entities, state);
```

AFTER:

The new method name `setAll` describes the intention better.

```ts
adapter.setAll(action.entities, state);
```

- refactor(data): use the setAll adapter method
- The initial state Injection Token for `@ngrx/component-store` has been renamed

BEFORE:

Injection Token is `initialStateToken`

AFTER:

Injection Token is `INITIAL_STATE_TOKEN`

<a name="10.0.1"></a>

## [10.0.1](https://github.com/ngrx/platform/compare/10.0.0...10.0.1) (2020-10-07)

### Bug Fixes

- **component:** add entry point for schematic ([#2688](https://github.com/ngrx/platform/issues/2688)) ([d937275](https://github.com/ngrx/platform/commit/d937275)), closes [#2683](https://github.com/ngrx/platform/issues/2683)
- **component-store:** add entry point for schematic ([#2687](https://github.com/ngrx/platform/issues/2687)) ([f8928e3](https://github.com/ngrx/platform/commit/f8928e3)), closes [#2682](https://github.com/ngrx/platform/issues/2682)
- **schematics:** prevent ng-add from rewriting other workspace cli options ([#2731](https://github.com/ngrx/platform/issues/2731)) ([37354aa](https://github.com/ngrx/platform/commit/37354aa))
- **store:** prevent unexpected behavior of {} as a props type ([#2728](https://github.com/ngrx/platform/issues/2728)) ([63510a8](https://github.com/ngrx/platform/commit/63510a8))

<a name="10.0.0"></a>

# [10.0.0](https://github.com/ngrx/platform/compare/10.0.0-rc.0...10.0.0) (2020-08-10)

<a name="10.0.0-rc.0"></a>

# [10.0.0-rc.0](https://github.com/ngrx/platform/compare/10.0.0-beta.1...10.0.0-rc.0) (2020-08-06)

### Bug Fixes

- **router-store:** add safety check to schematic ([#2632](https://github.com/ngrx/platform/issues/2632)) ([255e9e8](https://github.com/ngrx/platform/commit/255e9e8))

### Code Refactoring

- **component-store:** fine-tune effect types ([#2645](https://github.com/ngrx/platform/issues/2645)) ([ee92912](https://github.com/ngrx/platform/commit/ee92912))

### Features

- **entity:** add mapOne adapter method ([#2628](https://github.com/ngrx/platform/issues/2628)) ([d1891ad](https://github.com/ngrx/platform/commit/d1891ad)), closes [#2538](https://github.com/ngrx/platform/issues/2538)

### BREAKING CHANGES

- **component-store:** EffectReturnFn has been removed and the effect type is stricter and more predictable.

BEFORE:

If effect was const e = effect((o: Observable<string>) => ....) it was still possible to call e() without passing any strings

AFTER:

If effect was const e = effect((o: Observable<string>) => ....) its not allowed to call e() without passing any strings

<a name="10.0.0-beta.1"></a>

# [10.0.0-beta.1](https://github.com/ngrx/platform/compare/10.0.0-beta.0...10.0.0-beta.1) (2020-07-20)

### Bug Fixes

- **example-app:** update snapshot ([f2af688](https://github.com/ngrx/platform/commit/f2af688))
- **schematics:** fix unit tests for JSON with comments ([155ec1c](https://github.com/ngrx/platform/commit/155ec1c))

### Features

- **component:** add ng-add and ng-update schematics ([#2611](https://github.com/ngrx/platform/issues/2611)) ([3f2bea4](https://github.com/ngrx/platform/commit/3f2bea4))
- **component-store:** add config for debounce selectors ([#2606](https://github.com/ngrx/platform/issues/2606)) ([ddf0271](https://github.com/ngrx/platform/commit/ddf0271))
- **component-store:** add imperative reads ([#2614](https://github.com/ngrx/platform/issues/2614)) ([2146774](https://github.com/ngrx/platform/commit/2146774))
- **component-store:** add ng-add and ng-update schematics ([#2598](https://github.com/ngrx/platform/issues/2598)) ([af7b2cc](https://github.com/ngrx/platform/commit/af7b2cc)), closes [#2569](https://github.com/ngrx/platform/issues/2569)

### schematics

- remove skipTest option ([#2596](https://github.com/ngrx/platform/issues/2596)) ([60cd5cc](https://github.com/ngrx/platform/commit/60cd5cc)), closes [#2561](https://github.com/ngrx/platform/issues/2561)

### BREAKING CHANGES

- The skipTest option has been renamed to skipTests

BEFORE:

ng generate container UsersPage --skipTest

AFTER:

ng generate container UsersPage --skipTests

<a name="10.0.0-beta.0"></a>

# [10.0.0-beta.0](https://github.com/ngrx/platform/compare/9.2.0...10.0.0-beta.0) (2020-06-25)

### Bug Fixes

- **component:** detect zone.js using instanceof comparison ([#2547](https://github.com/ngrx/platform/issues/2547)) ([7128667](https://github.com/ngrx/platform/commit/7128667))
- **component:** removed ivy checks as obsolete ([#2579](https://github.com/ngrx/platform/issues/2579)) ([e239950](https://github.com/ngrx/platform/commit/e239950))
- **component-store:** export EffectReturnFn interface ([#2555](https://github.com/ngrx/platform/issues/2555)) ([f2a2212](https://github.com/ngrx/platform/commit/f2a2212))
- **data:** mergeQuerySet uses mergeStrategy ([#2430](https://github.com/ngrx/platform/issues/2430)) ([e1720b4](https://github.com/ngrx/platform/commit/e1720b4)), closes [#2368](https://github.com/ngrx/platform/issues/2368)
- **entity:** remove incorrect ComparerStr type ([#2584](https://github.com/ngrx/platform/issues/2584)) ([4796c97](https://github.com/ngrx/platform/commit/4796c97))
- **schematics:** add comma before devtools for empty imports ([#2542](https://github.com/ngrx/platform/issues/2542)) ([f2d4ebc](https://github.com/ngrx/platform/commit/f2d4ebc))

### Chores

- update Angular dependencies to latest v10 RC ([#2573](https://github.com/ngrx/platform/issues/2573)) ([ed28449](https://github.com/ngrx/platform/commit/ed28449))

### Features

- **component-store:** add support for selectors ([#2539](https://github.com/ngrx/platform/issues/2539)) ([47e7ba3](https://github.com/ngrx/platform/commit/47e7ba3))
- **component-store:** add support for side effects ([#2544](https://github.com/ngrx/platform/issues/2544)) ([f892cc8](https://github.com/ngrx/platform/commit/f892cc8))
- **component-store:** make library compatible with ViewEngine ([#2580](https://github.com/ngrx/platform/issues/2580)) ([ba0818e](https://github.com/ngrx/platform/commit/ba0818e))
- **router-store:** add route fragment selector ([#2543](https://github.com/ngrx/platform/issues/2543)) ([aba7368](https://github.com/ngrx/platform/commit/aba7368))

### Performance Improvements

- **component-store:** push updates to queueScheduler and single selectors to asapSchedulers ([#2586](https://github.com/ngrx/platform/issues/2586)) ([58073ab](https://github.com/ngrx/platform/commit/58073ab))

### BREAKING CHANGES

- **entity:** The compare function is used in two places, neither of which expect it to be able to return a string:
  The first caller is the Array prototype sort function, and there it "should return a negative, zero, or positive value, depending on the arguments".
  The second caller does a numerical comparison with the result.

Even though an id can be a string, the result of a comparison shouldn't be.

BEFORE:

The sortComparer types allow for a string to be returned

AFTER:

The sortComparer types only allow a number to be returned

- BEFORE:

Angular v9 are minimum dependencies

AFTER:

Angular v10 are minimum dependencies

<a name="9.2.0"></a>

# [9.2.0](https://github.com/ngrx/platform/compare/9.1.2...9.2.0) (2020-05-28)

### Bug Fixes

- **router-store:** selects should return selectors ([#2517](https://github.com/ngrx/platform/issues/2517)) ([831e1e4](https://github.com/ngrx/platform/commit/831e1e4)), closes [#2516](https://github.com/ngrx/platform/issues/2516)
- **schematics:** components should inject the store without generic ([#2512](https://github.com/ngrx/platform/issues/2512)) ([4f7dcdc](https://github.com/ngrx/platform/commit/4f7dcdc))
- **schematics:** use skipTests flag consistently, deprecate skipTest option ([#2522](https://github.com/ngrx/platform/issues/2522)) ([83033d7](https://github.com/ngrx/platform/commit/83033d7)), closes [#2521](https://github.com/ngrx/platform/issues/2521)
- **store:** remove circular dependency for mock import ([#2540](https://github.com/ngrx/platform/issues/2540)) ([4892fa2](https://github.com/ngrx/platform/commit/4892fa2))

### Features

- **component:** add ngrxPush migration ([#2452](https://github.com/ngrx/platform/issues/2452)) ([0775093](https://github.com/ngrx/platform/commit/0775093)), closes [#2450](https://github.com/ngrx/platform/issues/2450)
- **component-store:** add initial setup ([#2519](https://github.com/ngrx/platform/issues/2519)) ([a2657ac](https://github.com/ngrx/platform/commit/a2657ac))
- **component-store:** initialization + updater/setState ([#2528](https://github.com/ngrx/platform/issues/2528)) ([3545df2](https://github.com/ngrx/platform/commit/3545df2))
- **effects:** catch action creators being returned in effect without being called ([#2536](https://github.com/ngrx/platform/issues/2536)) ([100970b](https://github.com/ngrx/platform/commit/100970b))
- **store:** add ngrxMockEnvironment function to control output during testing ([#2513](https://github.com/ngrx/platform/issues/2513)) ([da1a0c0](https://github.com/ngrx/platform/commit/da1a0c0)), closes [#2363](https://github.com/ngrx/platform/issues/2363)
- **store:** add runtime check for action type uniqueness ([#2520](https://github.com/ngrx/platform/issues/2520)) ([2972980](https://github.com/ngrx/platform/commit/2972980))

<a name="9.1.2"></a>

## [9.1.2](https://github.com/ngrx/platform/compare/9.1.1...9.1.2) (2020-05-06)

<a name="9.1.1"></a>

## [9.1.1](https://github.com/ngrx/platform/compare/9.1.0...9.1.1) (2020-05-05)

### Bug Fixes

- **router-store:** selectors should return MemoizedSelector ([#2492](https://github.com/ngrx/platform/issues/2492)) ([39a4b91](https://github.com/ngrx/platform/commit/39a4b91))
- **schematics:** use Angular default properties when not defined ([#2507](https://github.com/ngrx/platform/issues/2507)) ([7cd0624](https://github.com/ngrx/platform/commit/7cd0624)), closes [#1036](https://github.com/ngrx/platform/issues/1036)
- **store:** ignore Ivy in runtime checks ([#2491](https://github.com/ngrx/platform/issues/2491)) ([46d752f](https://github.com/ngrx/platform/commit/46d752f)), closes [#2404](https://github.com/ngrx/platform/issues/2404)

<a name="9.1.0"></a>

# [9.1.0](https://github.com/ngrx/platform/compare/9.0.0...9.1.0) (2020-04-07)

### Bug Fixes

- **component:** add docs overview ([#2444](https://github.com/ngrx/platform/issues/2444)) ([a279dd1](https://github.com/ngrx/platform/commit/a279dd1)), closes [#2442](https://github.com/ngrx/platform/issues/2442)
- **example:** optimistically add/remove book from collection ([#2429](https://github.com/ngrx/platform/issues/2429)) ([b0aacf7](https://github.com/ngrx/platform/commit/b0aacf7)), closes [#2417](https://github.com/ngrx/platform/issues/2417)
- **schematics:** install v9 with ng-add ([#2455](https://github.com/ngrx/platform/issues/2455)) ([19f1bda](https://github.com/ngrx/platform/commit/19f1bda))
- **toObservableValue:** accommodate all observable inputs ([#2471](https://github.com/ngrx/platform/issues/2471)) ([468303a](https://github.com/ngrx/platform/commit/468303a))

### Features

- **component:** add ngrxPush pipe and ngrxLet directive to [@ngrx](https://github.com/ngrx)/component package ([#2046](https://github.com/ngrx/platform/issues/2046)) ([464073d](https://github.com/ngrx/platform/commit/464073d))
- **effects:** add user provided effects to EffectsModule.forFeature ([#2231](https://github.com/ngrx/platform/issues/2231)) ([59ce3e2](https://github.com/ngrx/platform/commit/59ce3e2)), closes [#2232](https://github.com/ngrx/platform/issues/2232)
- **schematics:** export reducer directly when Ivy is enabled ([#2440](https://github.com/ngrx/platform/issues/2440)) ([b68fa67](https://github.com/ngrx/platform/commit/b68fa67))

<a name="9.0.0"></a>

# [9.0.0](https://github.com/ngrx/platform/compare/9.0.0-rc.0...9.0.0) (2020-03-09)

### Features

- **effects:** add EffectsRunner to public API ([#2427](https://github.com/ngrx/platform/issues/2427)) ([f66fd64](https://github.com/ngrx/platform/commit/f66fd64))

<a name="9.0.0-rc.0"></a>

# [9.0.0-rc.0](https://github.com/ngrx/platform/compare/9.0.0-beta.2...9.0.0-rc.0) (2020-03-02)

### Bug Fixes

- **data:** correct AppEntityServices example in ngrx data doc page ([#2413](https://github.com/ngrx/platform/issues/2413)) ([711ba0e](https://github.com/ngrx/platform/commit/711ba0e)), closes [#2280](https://github.com/ngrx/platform/issues/2280)
- **example:** fix a typo selectShowSidenav ([#2414](https://github.com/ngrx/platform/issues/2414)) ([c9ebb06](https://github.com/ngrx/platform/commit/c9ebb06))

### Features

- **entity:** add 'setOne' method to entity adapter ([#2410](https://github.com/ngrx/platform/issues/2410)) ([4b4bb85](https://github.com/ngrx/platform/commit/4b4bb85)), closes [#2369](https://github.com/ngrx/platform/issues/2369)

<a name="9.0.0-beta.2"></a>

# [9.0.0-beta.2](https://github.com/ngrx/platform/compare/9.0.0-beta.1...9.0.0-beta.2) (2020-02-25)

### Bug Fixes

- **docs:** replace duplicate link ([#2399](https://github.com/ngrx/platform/issues/2399)) ([d4502b4](https://github.com/ngrx/platform/commit/d4502b4))
- **effects:** use source instance for ngrxOnRunEffects to retain context ([#2401](https://github.com/ngrx/platform/issues/2401)) ([79c830c](https://github.com/ngrx/platform/commit/79c830c))

### Features

- **store-devtools:** add INITIAL_OPTIONS to public API ([#2405](https://github.com/ngrx/platform/issues/2405)) ([37f91db](https://github.com/ngrx/platform/commit/37f91db)), closes [#1470](https://github.com/ngrx/platform/issues/1470)

<a name="9.0.0-beta.1"></a>

# [9.0.0-beta.1](https://github.com/ngrx/platform/compare/9.0.0-beta.0...9.0.0-beta.1) (2020-02-18)

### Bug Fixes

- **data:** Angular 9 style ModuleWithProvider ([#2356](https://github.com/ngrx/platform/issues/2356)) ([#2357](https://github.com/ngrx/platform/issues/2357)) ([182f140](https://github.com/ngrx/platform/commit/182f140))
- **data:** change type of filter observable ([#2349](https://github.com/ngrx/platform/issues/2349)) ([94f3ef1](https://github.com/ngrx/platform/commit/94f3ef1)), closes [#2337](https://github.com/ngrx/platform/issues/2337)
- **data:** EntityDataModuleWithoutEffect ModuleWithProviders ([#2366](https://github.com/ngrx/platform/issues/2366)) ([234ce84](https://github.com/ngrx/platform/commit/234ce84))
- **data:** make mergeServerUpserts change state immutably ([#2374](https://github.com/ngrx/platform/issues/2374)) ([#2389](https://github.com/ngrx/platform/issues/2389)) ([b3a49c1](https://github.com/ngrx/platform/commit/b3a49c1))
- **data:** make undoMany remove tracking changes in changeState ([#2346](https://github.com/ngrx/platform/issues/2346)) ([#2352](https://github.com/ngrx/platform/issues/2352)) ([637b2c7](https://github.com/ngrx/platform/commit/637b2c7))
- **data:** use ng_package for bundling instead of pkg_npm ([9a935b1](https://github.com/ngrx/platform/commit/9a935b1))
- **effects:** dispatch OnInitEffects action after registration ([#2386](https://github.com/ngrx/platform/issues/2386)) ([daf1e64](https://github.com/ngrx/platform/commit/daf1e64)), closes [#2373](https://github.com/ngrx/platform/issues/2373)
- **store:** provide the same instance of MockStore ([#2381](https://github.com/ngrx/platform/issues/2381)) ([827f336](https://github.com/ngrx/platform/commit/827f336)), closes [#2362](https://github.com/ngrx/platform/issues/2362)

### Features

- **effects:** limit retries to 10 by default ([#2376](https://github.com/ngrx/platform/issues/2376)) ([88124a7](https://github.com/ngrx/platform/commit/88124a7)), closes [#2303](https://github.com/ngrx/platform/issues/2303)
- **store:** add strictActionWithinNgZone runtime check ([#2364](https://github.com/ngrx/platform/issues/2364)) ([4cae255](https://github.com/ngrx/platform/commit/4cae255)), closes [#2339](https://github.com/ngrx/platform/issues/2339)
- **store:** testing - clean up mock store and remove static property ([#2361](https://github.com/ngrx/platform/issues/2361)) ([ee2c114](https://github.com/ngrx/platform/commit/ee2c114))

<a name="9.0.0-beta.0"></a>

# [9.0.0-beta.0](https://github.com/ngrx/platform/compare/8.6.0...9.0.0-beta.0) (2020-02-06)

### Bug Fixes

- **data:** allow additional selectors in entitySelectors$ ([#2332](https://github.com/ngrx/platform/issues/2332)) ([900bf75](https://github.com/ngrx/platform/commit/900bf75))
- **effects:** dispatch init action once ([#2164](https://github.com/ngrx/platform/issues/2164)) ([a528320](https://github.com/ngrx/platform/commit/a528320)), closes [#2106](https://github.com/ngrx/platform/issues/2106)
- **effects:** fix specs for ng-add tests ([#2314](https://github.com/ngrx/platform/issues/2314)) ([98d6606](https://github.com/ngrx/platform/commit/98d6606))
- **schematics:** migrate spec to skipTest to be in line with Angular CLI ([#2253](https://github.com/ngrx/platform/issues/2253)) ([714ae5f](https://github.com/ngrx/platform/commit/714ae5f)), closes [#2242](https://github.com/ngrx/platform/issues/2242)
- **store:** add not allowed check to action creator config ([#2313](https://github.com/ngrx/platform/issues/2313)) ([f6336d5](https://github.com/ngrx/platform/commit/f6336d5))
- **store:** allow union of types in props ([#2301](https://github.com/ngrx/platform/issues/2301)) ([33241cb](https://github.com/ngrx/platform/commit/33241cb))
- **store:** replace Creator with ActionCreator on createAction ([#2299](https://github.com/ngrx/platform/issues/2299)) ([fe6bfa7](https://github.com/ngrx/platform/commit/fe6bfa7))

### Chores

- update deps to Angular version 9 ([#2234](https://github.com/ngrx/platform/issues/2234)) ([b146af5](https://github.com/ngrx/platform/commit/b146af5))

### Code Refactoring

- **schematics:** Flag minimal is set to true ([#2258](https://github.com/ngrx/platform/issues/2258)) ([7ecaa22](https://github.com/ngrx/platform/commit/7ecaa22)), closes [#2250](https://github.com/ngrx/platform/issues/2250)
- **schematics:** migrate from styleext to style ([#2254](https://github.com/ngrx/platform/issues/2254)) ([2801018](https://github.com/ngrx/platform/commit/2801018)), closes [#2248](https://github.com/ngrx/platform/issues/2248)

### Features

- **component:** initial setup ([#2257](https://github.com/ngrx/platform/issues/2257)) ([b8a769a](https://github.com/ngrx/platform/commit/b8a769a))
- **docs:** add presskit page ([#2296](https://github.com/ngrx/platform/issues/2296)) ([9ac1165](https://github.com/ngrx/platform/commit/9ac1165)), closes [#2293](https://github.com/ngrx/platform/issues/2293)
- **effects:** add migration for breaking change that renames effects error handler config key ([#2335](https://github.com/ngrx/platform/issues/2335)) ([93b4081](https://github.com/ngrx/platform/commit/93b4081))
- **effects:** make resubscription handler overridable ([#2295](https://github.com/ngrx/platform/issues/2295)) ([3a9ad63](https://github.com/ngrx/platform/commit/3a9ad63)), closes [#2294](https://github.com/ngrx/platform/issues/2294)
- **entity:** deprecate addAll and rename it to setAll ([#2348](https://github.com/ngrx/platform/issues/2348)) ([27f5059](https://github.com/ngrx/platform/commit/27f5059)), closes [#2330](https://github.com/ngrx/platform/issues/2330)
- **router:** enabling MinimalRouterStateSerializer by default ([#2326](https://github.com/ngrx/platform/issues/2326)) ([ba37ad8](https://github.com/ngrx/platform/commit/ba37ad8)), closes [#2225](https://github.com/ngrx/platform/issues/2225)
- **router-store:** add migration to add the default serializer ([#2291](https://github.com/ngrx/platform/issues/2291)) ([b742a8c](https://github.com/ngrx/platform/commit/b742a8c))
- **schematics:** update creators to the default ([6149753](https://github.com/ngrx/platform/commit/6149753))
- **store:** add default generic type to Store and MockStore ([#2325](https://github.com/ngrx/platform/issues/2325)) ([09daeb9](https://github.com/ngrx/platform/commit/09daeb9))
- **store:** ignore actions from NgRx libraries in runtime checks ([#2351](https://github.com/ngrx/platform/issues/2351)) ([0dabfc4](https://github.com/ngrx/platform/commit/0dabfc4))
- update to Angular 9-rc.13 ([#2345](https://github.com/ngrx/platform/issues/2345)) ([d7fdf7f](https://github.com/ngrx/platform/commit/d7fdf7f))
- **store:** add clearResult to reset a mock selector ([#2270](https://github.com/ngrx/platform/issues/2270)) ([803295b](https://github.com/ngrx/platform/commit/803295b)), closes [#2244](https://github.com/ngrx/platform/issues/2244)
- **store:** compile time errors when action creators being passed to dispatch without () ([#2306](https://github.com/ngrx/platform/issues/2306)) ([98b74ad](https://github.com/ngrx/platform/commit/98b74ad))
- **store:** enable immutability checks by default ([#2266](https://github.com/ngrx/platform/issues/2266)) ([1758d34](https://github.com/ngrx/platform/commit/1758d34)), closes [#2217](https://github.com/ngrx/platform/issues/2217)
- **store:** testing - expose MockStore provider ([#2331](https://github.com/ngrx/platform/issues/2331)) ([ef5cd5f](https://github.com/ngrx/platform/commit/ef5cd5f)), closes [#2328](https://github.com/ngrx/platform/issues/2328)

### BREAKING CHANGES

- **router:** The MinimalRouterStateSerializer is enabled by default.

BEFORE:

If no router state serializer is provided through the configuration of router store, the DefaultRouterStateSerializer is used.

AFTER:

If no router state serializer is provided through the configuration of router store, the MinimalRouterStateSerializer is used.

- **effects:** `resubscribeOnError` renamed to `useEffectsErrorHandler` in `createEffect` metadata

BEFORE:

```ts
class MyEffects {
  effect$ = createEffect(() => stream$, {
    resubscribeOnError: true, // default
  });
}
```

AFTER:

```ts
class MyEffects {
  effect$ = createEffect(() => stream$, {
    useEffectsErrorHandler: true, // default
  });
}
```

- **effects:** BEFORE:

When the effect class was registered, the init action would be dispatched.
If the effect was provided in multiple lazy loaded modules, the init action would be dispatched for every module.

AFTER:

The init action is only dispatched once
The init action is now dispatched based on the identifier of the effect (via ngrxOnIdentifyEffects)

- **schematics:** To be inline with the Angular CLI, we migrated the `--spec` to `--skipTest`.
  By default skipTest is false, this way you will always be provided with `*.spec.ts files`

BEFORE:

```sh

ng generate action User --spec

```

AFTER:

```sh

ng generate action User

```

- **store:** BEFORE:

Using `mockSelector.setResult(undefined)` resulted in clearing the
return value.

AFTER:

Using `mockSelector.setResult(undefined)` will set the return value of
the selector to `undefined`.
To reset the mock selector, use `mockSelector.clearResult()`.

- **schematics:** To be inline with the Angular CLI, the `styleExt` option has been changed to `style`.

BEFORE:

```ts
"@schematics/angular:component": {
      "inlineStyle": true,
      "prefix": "aio",
      "styleext": "scss"
    }
...
```

AFTER:

```ts
"@schematics/angular:component": {
      "inlineStyle": true,
      "prefix": "aio",
      "style": "scss"
    }
....
```

- **store:** Immutability checks are enabled by default.

BEFORE:

Immutability checks are opt-in.

AFTER:

If state or action is mutated then there will be a run time exception thrown.

- **schematics:** With this change by default the minimal setup for `@ngrx/store` will be generated.

BEFORE:

```ts
@NgModule({
  declarations: [
    AppComponent,
  ],
  imports: [
    BrowserModule,
    StoreModule.forRoot(reducers, {
      metaReducers,
      runtimeChecks: {
        strictStateImmutability: true,
        strictActionImmutability: true
      }
    }),
    .....
  ],
  providers: [],
  bootstrap: [AppComponent]
})
```

AFTER:

```ts
@NgModule({
  declarations: [
    AppComponent,
  ],
  imports: [
    BrowserModule,
    StoreModule.forRoot({})
    ....
  ],
  providers: [],
  bootstrap: [AppComponent]
})
```

- **schematics:** BEFORE:

The create functions weren't the default to create actions, reducers and effects

AFTER:

The create functions are the default to create actions (createAction, reducers (createReducer) and effects (createEffect)
To fallback to the previous generators, use

`sh
ng generate reducer ReducerName --creators=false
`

- Libraries will depend on Angular version 9

<a name="8.6.0"></a>

# [8.6.0](https://github.com/ngrx/platform/compare/8.5.2...8.6.0) (2019-12-18)

### Features

- **router-store:** add action creator for root router actions ([#2272](https://github.com/ngrx/platform/issues/2272)) ([f17589f](https://github.com/ngrx/platform/commit/f17589f)), closes [#2206](https://github.com/ngrx/platform/issues/2206)

<a name="8.5.2"></a>

## [8.5.2](https://github.com/ngrx/platform/compare/8.5.1...8.5.2) (2019-11-21)

### Bug Fixes

- **effects:** add EffectsRootModule and EffectsFeatureModule to public API ([#2273](https://github.com/ngrx/platform/issues/2273)) ([abe1f6b](https://github.com/ngrx/platform/commit/abe1f6b))
- **store:** added noop for addFeature in MockReducerManager ([#2265](https://github.com/ngrx/platform/issues/2265)) ([c42e444](https://github.com/ngrx/platform/commit/c42e444)), closes [#2263](https://github.com/ngrx/platform/issues/2263)
- **store-devtools:** escaping the safelist and blocklist strings ([#2259](https://github.com/ngrx/platform/issues/2259)) ([e888977](https://github.com/ngrx/platform/commit/e888977)), closes [#2228](https://github.com/ngrx/platform/issues/2228)

<a name="8.5.1"></a>

## [8.5.1](https://github.com/ngrx/platform/compare/8.5.0...8.5.1) (2019-11-12)

### Bug Fixes

- **effects:** add action creator for root effects init action ([#2219](https://github.com/ngrx/platform/issues/2219)) ([de9a590](https://github.com/ngrx/platform/commit/de9a590)), closes [#2218](https://github.com/ngrx/platform/issues/2218)
- **effects:** export CreateEffectMetadata ([#2245](https://github.com/ngrx/platform/issues/2245)) ([bfe4c81](https://github.com/ngrx/platform/commit/bfe4c81)), closes [#2243](https://github.com/ngrx/platform/issues/2243)

<a name="8.5.0"></a>

# [8.5.0](https://github.com/ngrx/platform/compare/8.4.0...8.5.0) (2019-11-07)

### Bug Fixes

- **effects:** resubscribe every time an error occurs ([#2165](https://github.com/ngrx/platform/issues/2165)) ([0d59783](https://github.com/ngrx/platform/commit/0d59783))
- **store:** disallow arrays in action creators ([#2155](https://github.com/ngrx/platform/issues/2155)) ([1e4c0be](https://github.com/ngrx/platform/commit/1e4c0be))
- **store:** improve createFeatureSelector warning ([#2163](https://github.com/ngrx/platform/issues/2163)) ([e4765d6](https://github.com/ngrx/platform/commit/e4765d6)), closes [#2116](https://github.com/ngrx/platform/issues/2116)
- **store:** improve types for string selectors ([#2174](https://github.com/ngrx/platform/issues/2174)) ([46a8467](https://github.com/ngrx/platform/commit/46a8467))

### Features

- **data:** add entity config in app module declaration for ng-add ([#2133](https://github.com/ngrx/platform/issues/2133)) ([6ca3056](https://github.com/ngrx/platform/commit/6ca3056))
- **effects:** createEffect returns specific type for dispatch false ([#2195](https://github.com/ngrx/platform/issues/2195)) ([f70600f](https://github.com/ngrx/platform/commit/f70600f))
- **effects:** improve types for ofType with action creators ([#2175](https://github.com/ngrx/platform/issues/2175)) ([cf02dd2](https://github.com/ngrx/platform/commit/cf02dd2))
- **schematics:** add message prompts for individual schematics ([#2143](https://github.com/ngrx/platform/issues/2143)) ([fcb01e2](https://github.com/ngrx/platform/commit/fcb01e2))
- **schematics:** add selector schematics ([#2160](https://github.com/ngrx/platform/issues/2160)) ([78817c7](https://github.com/ngrx/platform/commit/78817c7)), closes [#2140](https://github.com/ngrx/platform/issues/2140)
- **store:** add On interface to public api ([#2157](https://github.com/ngrx/platform/issues/2157)) ([1b4ba1a](https://github.com/ngrx/platform/commit/1b4ba1a))

<a name="8.4.0"></a>

# [8.4.0](https://github.com/ngrx/platform/compare/8.3.0...8.4.0) (2019-10-09)

### Bug Fixes

- **schematics:** fixed the schematics/action spec template ([#2092](https://github.com/ngrx/platform/issues/2092)) ([ed3b1f9](https://github.com/ngrx/platform/commit/ed3b1f9)), closes [#2082](https://github.com/ngrx/platform/issues/2082)
- **store:** improve consistency of memoized selector result when projection fails ([#2101](https://github.com/ngrx/platform/issues/2101)) ([c63941c](https://github.com/ngrx/platform/commit/c63941c)), closes [#2100](https://github.com/ngrx/platform/issues/2100)

### Features

- **effects:** throw error when forRoot() is used more than once ([b46748c](https://github.com/ngrx/platform/commit/b46748c))
- **schematics:** add createEffect migration schematic ([#2136](https://github.com/ngrx/platform/issues/2136)) ([9eb1bd5](https://github.com/ngrx/platform/commit/9eb1bd5))
- **store:** add refreshState method to mock store ([#2148](https://github.com/ngrx/platform/issues/2148)) ([30e876f](https://github.com/ngrx/platform/commit/30e876f)), closes [#2121](https://github.com/ngrx/platform/issues/2121)
- **store:** allow multiple on handlers for the same action in createReducer([#2103](https://github.com/ngrx/platform/issues/2103)) ([9a70262](https://github.com/ngrx/platform/commit/9a70262)), closes [#1956](https://github.com/ngrx/platform/issues/1956)
- **store:** cleanup selector after a test ([2964e2b](https://github.com/ngrx/platform/commit/2964e2b))
- **store:** throw error when forRoot() is used more than once ([4304865](https://github.com/ngrx/platform/commit/4304865))

<a name="8.3.0"></a>

# [8.3.0](https://github.com/ngrx/platform/compare/8.2.0...8.3.0) (2019-08-29)

### Bug Fixes

- **data:** use correct guard when handling optimistic update ([#2060](https://github.com/ngrx/platform/issues/2060)) ([34c0420](https://github.com/ngrx/platform/commit/34c0420)), closes [#2059](https://github.com/ngrx/platform/issues/2059)
- **store:** add DefaultProjectorFn to public API ([#2090](https://github.com/ngrx/platform/issues/2090)) ([2d37b48](https://github.com/ngrx/platform/commit/2d37b48))
- **store:** should not run schematics when not using named imports ([#2095](https://github.com/ngrx/platform/issues/2095)) ([7cadbc0](https://github.com/ngrx/platform/commit/7cadbc0)), closes [#2093](https://github.com/ngrx/platform/issues/2093)

### Features

- **store:** add verbose error message for undefined feature state in development mode ([#2078](https://github.com/ngrx/platform/issues/2078)) ([6946e2e](https://github.com/ngrx/platform/commit/6946e2e)), closes [#1897](https://github.com/ngrx/platform/issues/1897)

<a name="8.2.0"></a>

# [8.2.0](https://github.com/ngrx/platform/compare/8.1.0...8.2.0) (2019-07-31)

### Bug Fixes

- **effects:** resubscribe every time an error occurs ([#2023](https://github.com/ngrx/platform/issues/2023)) ([#2026](https://github.com/ngrx/platform/issues/2026)) ([5b48912](https://github.com/ngrx/platform/commit/5b48912))
- **store:** add missing StoreConfig and RootStoreConfig exports ([#2009](https://github.com/ngrx/platform/issues/2009)) ([5e01e50](https://github.com/ngrx/platform/commit/5e01e50)), closes [#2007](https://github.com/ngrx/platform/issues/2007)

### Features

- **docs:** enable search functionality ([#2020](https://github.com/ngrx/platform/issues/2020)) ([3cc4f3d](https://github.com/ngrx/platform/commit/3cc4f3d))
- **router-store:** add selectQueryParam and selectRouteParam ([#2014](https://github.com/ngrx/platform/issues/2014)) ([57fd3d7](https://github.com/ngrx/platform/commit/57fd3d7))
- **schematics:** add option to use MockStore in container tests ([#2029](https://github.com/ngrx/platform/issues/2029)) ([6905d52](https://github.com/ngrx/platform/commit/6905d52)), closes [#2028](https://github.com/ngrx/platform/issues/2028)
- **store:** add USER_RUNTIME_CHECKS public token ([#2006](https://github.com/ngrx/platform/issues/2006)) ([fa8da34](https://github.com/ngrx/platform/commit/fa8da34)), closes [#1973](https://github.com/ngrx/platform/issues/1973)

<a name="8.1.0"></a>

# [8.1.0](https://github.com/ngrx/platform/compare/8.0.1...8.1.0) (2019-07-09)

### Bug Fixes

- **data:** allow ChangeSetItemFactory to update entities with number ids ([#1995](https://github.com/ngrx/platform/issues/1995)) ([f11c7b2](https://github.com/ngrx/platform/commit/f11c7b2)), closes [#1988](https://github.com/ngrx/platform/issues/1988)
- **data:** search for replacements in all files when using ng-add ([#1971](https://github.com/ngrx/platform/issues/1971)) ([30ce2c6](https://github.com/ngrx/platform/commit/30ce2c6))
- **store:** add immutability check for IE compatibility ([#1997](https://github.com/ngrx/platform/issues/1997)) ([11c0864](https://github.com/ngrx/platform/commit/11c0864)), closes [#1991](https://github.com/ngrx/platform/issues/1991)
- **store:** fix typo in runtime checks injection token description ([#1975](https://github.com/ngrx/platform/issues/1975)) ([125d950](https://github.com/ngrx/platform/commit/125d950)), closes [#1972](https://github.com/ngrx/platform/issues/1972)

### Features

- **effects:** add support for minimal setup option for ng-add ([e839568](https://github.com/ngrx/platform/commit/e839568))
- **effects:** export EffectConfig and add docs ([6a4bbcf](https://github.com/ngrx/platform/commit/6a4bbcf))
- **schematics:** add support for minimal setup option for store and effects ([cede393](https://github.com/ngrx/platform/commit/cede393))
- **schematics:** enable immutability checks for root store by default ([#1983](https://github.com/ngrx/platform/issues/1983)) ([2b8178d](https://github.com/ngrx/platform/commit/2b8178d)), closes [#1950](https://github.com/ngrx/platform/issues/1950)
- **store:** add support for minimal setup option for ng-add ([12202a7](https://github.com/ngrx/platform/commit/12202a7))

<a name="8.0.1"></a>

## [8.0.1](https://github.com/ngrx/platform/compare/8.0.0...8.0.1) (2019-06-10)

### Bug Fixes

- **store:** prevent passing of action creator function to store dispatch and effects ([#1914](https://github.com/ngrx/platform/issues/1914)) ([78153cb](https://github.com/ngrx/platform/commit/78153cb)), closes [#1906](https://github.com/ngrx/platform/issues/1906)

<a name="8.0.0"></a>

# [8.0.0](https://github.com/ngrx/platform/compare/8.0.0-rc.1...8.0.0) (2019-06-06)

### Features

- **store:** add protection from type property use ([#1923](https://github.com/ngrx/platform/issues/1923)) ([bb9add7](https://github.com/ngrx/platform/commit/bb9add7)), closes [#1917](https://github.com/ngrx/platform/issues/1917)
- **store:** capture the type of a selector projector function ([#1920](https://github.com/ngrx/platform/issues/1920)) ([4e39cc1](https://github.com/ngrx/platform/commit/4e39cc1)), closes [#1908](https://github.com/ngrx/platform/issues/1908)

### Performance Improvements

- fine tune schematics to only commit changes ([#1925](https://github.com/ngrx/platform/issues/1925)) ([5fcdd3b](https://github.com/ngrx/platform/commit/5fcdd3b))

<a name="8.0.0-rc.1"></a>

# [8.0.0-rc.1](https://github.com/ngrx/platform/compare/8.0.0-rc.0...8.0.0-rc.1) (2019-06-04)

### Bug Fixes

- **router-store:** remove circular dependency in serializers ([#1904](https://github.com/ngrx/platform/issues/1904)) ([0407c5b](https://github.com/ngrx/platform/commit/0407c5b)), closes [#1902](https://github.com/ngrx/platform/issues/1902)

### Features

- **store:** add ngrx-store-freeze migration ([#1901](https://github.com/ngrx/platform/issues/1901)) ([4146650](https://github.com/ngrx/platform/commit/4146650)), closes [#1896](https://github.com/ngrx/platform/issues/1896)

<a name="8.0.0-rc.0"></a>

# [8.0.0-rc.0](https://github.com/ngrx/platform/compare/8.0.0-beta.2...8.0.0-rc.0) (2019-05-30)

### Bug Fixes

- update signature for createSelectorFactory and createSelector to return a MemoizedSelector ([#1883](https://github.com/ngrx/platform/issues/1883)) ([8b31da7](https://github.com/ngrx/platform/commit/8b31da7))
- **store:** adjust mock store to handle selectors with props ([#1878](https://github.com/ngrx/platform/issues/1878)) ([a7ded00](https://github.com/ngrx/platform/commit/a7ded00)), closes [#1864](https://github.com/ngrx/platform/issues/1864) [#1873](https://github.com/ngrx/platform/issues/1873)

### Features

- **effects:** resubscribe to effects on error ([#1881](https://github.com/ngrx/platform/issues/1881)) ([71137e5](https://github.com/ngrx/platform/commit/71137e5))
- **example:** add examples of effects not based on the Actions stream ([#1845](https://github.com/ngrx/platform/issues/1845)) ([3454e70](https://github.com/ngrx/platform/commit/3454e70)), closes [#1830](https://github.com/ngrx/platform/issues/1830)
- **router-store:** add routerState config option ([#1847](https://github.com/ngrx/platform/issues/1847)) ([d874cfc](https://github.com/ngrx/platform/commit/d874cfc)), closes [#1834](https://github.com/ngrx/platform/issues/1834)
- **router-store:** add selectors for router state ([#1874](https://github.com/ngrx/platform/issues/1874)) ([21c67cc](https://github.com/ngrx/platform/commit/21c67cc)), closes [#1854](https://github.com/ngrx/platform/issues/1854)
- **store:** split immutibility checks in state and action checks ([#1894](https://github.com/ngrx/platform/issues/1894)) ([c59c211](https://github.com/ngrx/platform/commit/c59c211))

### Reverts

- **store:** store should fail synchronously ([#1871](https://github.com/ngrx/platform/issues/1871)) ([59a9e6c](https://github.com/ngrx/platform/commit/59a9e6c)), closes [#1865](https://github.com/ngrx/platform/issues/1865)

### BREAKING CHANGES

- **effects:** Prior to introduction of automatic resubscriptions on errors, all effects had effectively {resubscribeOnError: false} behavior. For the rare cases when this is still wanted please add {resubscribeOnError: false} to the effect metadata.

BEFORE:

```ts
login$ = createEffect(() =>
  this.actions$.pipe(
    ofType(LoginPageActions.login),
    mapToAction(
      // Happy path callback
      (action) =>
        this.authService
          .login(action.credentials)
          .pipe(map((user) => AuthApiActions.loginSuccess({ user }))),
      // error callback
      (error) => AuthApiActions.loginFailure({ error })
    )
  )
);
```

AFTER:

```ts
login$ = createEffect(
  () =>
    this.actions$.pipe(
      ofType(LoginPageActions.login),
      mapToAction(
        // Happy path callback
        (action) =>
          this.authService
            .login(action.credentials)
            .pipe(
              map((user) => AuthApiActions.loginSuccess({ user }))
            ),
        // error callback
        (error) => AuthApiActions.loginFailure({ error })
      )
      // Errors are handled and it is safe to disable resubscription
    ),
  { resubscribeOnError: false }
);
```

- The return type of the createSelectorFactory and createSelector is now a MemoizedSelector instead of a Selector

<a name="8.0.0-beta.2"></a>

# [8.0.0-beta.2](https://github.com/ngrx/platform/compare/8.0.0-beta.1...8.0.0-beta.2) (2019-05-15)

### Bug Fixes

- **data:** update the package name for replacement to ngrx-data ([#1805](https://github.com/ngrx/platform/issues/1805)) ([00c00e0](https://github.com/ngrx/platform/commit/00c00e0)), closes [#1802](https://github.com/ngrx/platform/issues/1802)
- **example:** resolve circular dependency ([#1833](https://github.com/ngrx/platform/issues/1833)) ([1fbd59c](https://github.com/ngrx/platform/commit/1fbd59c))

### Features

- **effects:** add mapToAction operator ([#1822](https://github.com/ngrx/platform/issues/1822)) ([1ff986f](https://github.com/ngrx/platform/commit/1ff986f)), closes [#1224](https://github.com/ngrx/platform/issues/1224)
- **store:** add option to mock selectors in MockStoreConfig ([#1836](https://github.com/ngrx/platform/issues/1836)) ([070228c](https://github.com/ngrx/platform/commit/070228c)), closes [#1827](https://github.com/ngrx/platform/issues/1827)
- **store:** expand createReducer type signature to support up to ten action creators ([#1803](https://github.com/ngrx/platform/issues/1803)) ([63e4926](https://github.com/ngrx/platform/commit/63e4926))
- **store:** warn when same action is registered ([#1801](https://github.com/ngrx/platform/issues/1801)) ([ecda5f7](https://github.com/ngrx/platform/commit/ecda5f7)), closes [#1758](https://github.com/ngrx/platform/issues/1758)

### Reverts

- warn when same action is registered ([#1801](https://github.com/ngrx/platform/issues/1801)) ([#1841](https://github.com/ngrx/platform/issues/1841)) ([b07ae4e](https://github.com/ngrx/platform/commit/b07ae4e))

<a name="8.0.0-beta.1"></a>

# [8.0.0-beta.1](https://github.com/ngrx/platform/compare/8.0.0-beta.0...8.0.0-beta.1) (2019-04-24)

### Features

- **data:** add schematics and migrations ([#1782](https://github.com/ngrx/platform/issues/1782)) ([c79362d](https://github.com/ngrx/platform/commit/c79362d))
- **schematics:** add support for reducer creators ([#1785](https://github.com/ngrx/platform/issues/1785)) ([8a0a049](https://github.com/ngrx/platform/commit/8a0a049)), closes [#1764](https://github.com/ngrx/platform/issues/1764)
- **store:** change createReducer to avoid generic ([#1796](https://github.com/ngrx/platform/issues/1796)) ([8f2cb7b](https://github.com/ngrx/platform/commit/8f2cb7b))

<a name="8.0.0-beta.0"></a>

# [8.0.0-beta.0](https://github.com/ngrx/platform/compare/7.4.0...8.0.0-beta.0) (2019-04-17)

### Bug Fixes

- **effects:** add the export of EffectMetadata ([#1720](https://github.com/ngrx/platform/issues/1720)) ([214316f](https://github.com/ngrx/platform/commit/214316f))
- **example:** handle possible undefined results from Dictionary ([#1745](https://github.com/ngrx/platform/issues/1745)) ([861b0cb](https://github.com/ngrx/platform/commit/861b0cb)), closes [#1735](https://github.com/ngrx/platform/issues/1735)
- **schematics:** check for empty name when using store schematic for feature states ([#1659](https://github.com/ngrx/platform/issues/1659)) ([#1666](https://github.com/ngrx/platform/issues/1666)) ([3b9b890](https://github.com/ngrx/platform/commit/3b9b890))
- **store:** add the missing bracket in immutability meta-reducer ([#1721](https://github.com/ngrx/platform/issues/1721)) ([56f8a59](https://github.com/ngrx/platform/commit/56f8a59))
- **Store:** selector with only a projector ([#1579](https://github.com/ngrx/platform/issues/1579)) ([da1ec80](https://github.com/ngrx/platform/commit/da1ec80)), closes [#1558](https://github.com/ngrx/platform/issues/1558)
- **StoreDevTools:** rename action list filters ([#1589](https://github.com/ngrx/platform/issues/1589)) ([5581826](https://github.com/ngrx/platform/commit/5581826)), closes [#1557](https://github.com/ngrx/platform/issues/1557)

### Code Refactoring

- **Store:** don't export internal functions and tokens ([#1679](https://github.com/ngrx/platform/issues/1679)) ([0446a15](https://github.com/ngrx/platform/commit/0446a15)), closes [#1657](https://github.com/ngrx/platform/issues/1657)

### Features

- **schematics:** add support for action creators to schematics ([#1765](https://github.com/ngrx/platform/issues/1765)) ([876f80a](https://github.com/ngrx/platform/commit/876f80a)), closes [#1670](https://github.com/ngrx/platform/issues/1670)
- **store:** add createReducer function ([#1746](https://github.com/ngrx/platform/issues/1746)) ([f954e14](https://github.com/ngrx/platform/commit/f954e14)), closes [#1724](https://github.com/ngrx/platform/issues/1724)
- introduce [@ngrx](https://github.com/ngrx)/data library to the platform ([#1733](https://github.com/ngrx/platform/issues/1733)) ([5d569c3](https://github.com/ngrx/platform/commit/5d569c3))
- introduce [@ngrx](https://github.com/ngrx)/data library to the platform ([#1754](https://github.com/ngrx/platform/issues/1754)) ([dbfdbaf](https://github.com/ngrx/platform/commit/dbfdbaf))
- **effects:** add createEffect function ([#1667](https://github.com/ngrx/platform/issues/1667)) ([ced2d3d](https://github.com/ngrx/platform/commit/ced2d3d)), closes [#1368](https://github.com/ngrx/platform/issues/1368)
- **effects:** allow non-dispatching effects to not return an action ([#1689](https://github.com/ngrx/platform/issues/1689)) ([04e07a6](https://github.com/ngrx/platform/commit/04e07a6))
- **effects:** allow ofType to handle ActionCreator ([#1676](https://github.com/ngrx/platform/issues/1676)) ([a41d1d6](https://github.com/ngrx/platform/commit/a41d1d6))
- **entity:** add undefined to Dictionary's index signature ([#1719](https://github.com/ngrx/platform/issues/1719)) ([d472757](https://github.com/ngrx/platform/commit/d472757))
- **example:** update ofType in effects per [#1676](https://github.com/ngrx/platform/issues/1676) ([#1691](https://github.com/ngrx/platform/issues/1691)) ([c9c9a0e](https://github.com/ngrx/platform/commit/c9c9a0e))
- **router-store:** add v8 migration schematic ([#1699](https://github.com/ngrx/platform/issues/1699)) ([0b794ce](https://github.com/ngrx/platform/commit/0b794ce))
- **router-store:** Make usage of forRoot required ([#1662](https://github.com/ngrx/platform/issues/1662)) ([#1672](https://github.com/ngrx/platform/issues/1672)) ([c7e1406](https://github.com/ngrx/platform/commit/c7e1406))
- **schematics:** add support for effect creators to schematics ([#1725](https://github.com/ngrx/platform/issues/1725)) ([8901abd](https://github.com/ngrx/platform/commit/8901abd)), closes [#1682](https://github.com/ngrx/platform/issues/1682)
- **store:** add API to mock selectors ([#1688](https://github.com/ngrx/platform/issues/1688)) ([2a9b067](https://github.com/ngrx/platform/commit/2a9b067)), closes [#1504](https://github.com/ngrx/platform/issues/1504)
- **store:** add immutability and serializability runtime checks ([#1613](https://github.com/ngrx/platform/issues/1613)) ([60633b7](https://github.com/ngrx/platform/commit/60633b7)), closes [#857](https://github.com/ngrx/platform/issues/857)
- **store:** add META_REDUCERS replacement migration ([#1640](https://github.com/ngrx/platform/issues/1640)) ([57bacf5](https://github.com/ngrx/platform/commit/57bacf5))
- **store:** run migration schema for v8 beta ([#1716](https://github.com/ngrx/platform/issues/1716)) ([0abc948](https://github.com/ngrx/platform/commit/0abc948))

### BREAKING CHANGES

- **entity:** Dictionary could be producing undefined but previous typings were not explicit about it.
- **Store:** Internal functions and tokens are removed from the public API
- **router-store:** usage of forRoot is now required for StoreRouterConnectingModule

BEFORE:

```ts
@NgModule({
  imports: [StoreRouterConnectingModule],
})
export class AppModule {}
```

AFTER:

```ts
@NgModule({
  imports: [StoreRouterConnectingModule.forRoot()],
})
export class AppModule {}
```

- **Store:** Selectors with only a projector function aren't valid anymore.
  This change will make the usage more consistent.

BEFORE:

```ts
const getTodosById = createSelector(
  (state: TodoAppSchema, id: number) =>
    state.todos.find((p) => p.id === id)
);
```

AFTER:

```ts
const getTodosById = createSelector(
  (state: TodoAppSchema) => state.todos,
  (todos: Todo[], id: number) => todos.find((p) => p.id === id)
);
```

- **StoreDevTools:** `actionsWhitelist` is renamed to `actionsSafelist`
  `actionsBlacklist` is renamed to `actionsBlocklist`

BEFORE:

```ts
StoreDevtoolsModule.instrument({
  actionsWhitelist: ['...'],
  actionsBlacklist: ['...'],
});
```

AFTER:

```ts
StoreDevtoolsModule.instrument({
  actionsSafelist: ['...'],
  actionsBlocklist: ['...'],
});
```

<a name="7.4.0"></a>

# [7.4.0](https://github.com/ngrx/platform/compare/7.3.0...7.4.0) (2019-03-29)

### Bug Fixes

- **Example:** linter problems ([#1597](https://github.com/ngrx/platform/issues/1597)) ([4cfcc08](https://github.com/ngrx/platform/commit/4cfcc08))

### Features

- **example-app:** add visual testing with Applitools ([#1605](https://github.com/ngrx/platform/issues/1605)) ([8856210](https://github.com/ngrx/platform/commit/8856210))
- **schematics:** use plural for entity schematics reducer key ([#1596](https://github.com/ngrx/platform/issues/1596)) ([1e49530](https://github.com/ngrx/platform/commit/1e49530)), closes [#1412](https://github.com/ngrx/platform/issues/1412)
- **store:** add action creator functions ([#1654](https://github.com/ngrx/platform/issues/1654)) ([e7fe28b](https://github.com/ngrx/platform/commit/e7fe28b)), closes [#1480](https://github.com/ngrx/platform/issues/1480) [#1634](https://github.com/ngrx/platform/issues/1634)

<a name="7.3.0"></a>

# [7.3.0](https://github.com/ngrx/platform/compare/7.2.0...7.3.0) (2019-02-27)

### Bug Fixes

- **schematics:** type actions and avoid endless loop in effect schematic ([#1576](https://github.com/ngrx/platform/issues/1576)) ([5fbcb3c](https://github.com/ngrx/platform/commit/5fbcb3c)), closes [#1573](https://github.com/ngrx/platform/issues/1573)
- **store:** deprecate signature for selector with only a projector ([#1580](https://github.com/ngrx/platform/issues/1580)) ([e86c5f6](https://github.com/ngrx/platform/commit/e86c5f6))

### Features

- **schematics:** Add ng-add support with prompt for making our schematics default ([#1552](https://github.com/ngrx/platform/issues/1552)) ([01ff157](https://github.com/ngrx/platform/commit/01ff157))

<a name="7.2.0"></a>

# [7.2.0](https://github.com/ngrx/platform/compare/7.1.0...7.2.0) (2019-01-29)

### Bug Fixes

- **Entity:** add schematics to bazel build ([88d0ad5](https://github.com/ngrx/platform/commit/88d0ad5))
- **RouterStore:** add schematics to bazel build ([7465af9](https://github.com/ngrx/platform/commit/7465af9))
- **StoreDevTools:** out of bounds when actions are filtered ([#1532](https://github.com/ngrx/platform/issues/1532)) ([d532979](https://github.com/ngrx/platform/commit/d532979)), closes [#1522](https://github.com/ngrx/platform/issues/1522)

### Features

- **schematics:** add api success/failure effects/actions to ng generate feature ([#1530](https://github.com/ngrx/platform/issues/1530)) ([e17a787](https://github.com/ngrx/platform/commit/e17a787))
- **schematics:** bump platformVersion to ^7.0.0 per issue [#1489](https://github.com/ngrx/platform/issues/1489) ([#1527](https://github.com/ngrx/platform/issues/1527)) ([a71aa71](https://github.com/ngrx/platform/commit/a71aa71))

<a name="7.1.0"></a>

# [7.1.0](https://github.com/ngrx/platform/compare/7.0.0...7.1.0) (2019-01-21)

### Bug Fixes

- **store:** call metareducer with the user's config initial state ([#1498](https://github.com/ngrx/platform/issues/1498)) ([2aabe0f](https://github.com/ngrx/platform/commit/2aabe0f)), closes [#1464](https://github.com/ngrx/platform/issues/1464)
- **store:** don't call the projector function if there are no selectors and props ([#1515](https://github.com/ngrx/platform/issues/1515)) ([e0ad3c3](https://github.com/ngrx/platform/commit/e0ad3c3)), closes [#1501](https://github.com/ngrx/platform/issues/1501)

### Features

- **example:** make the example app more user friendly ([#1508](https://github.com/ngrx/platform/issues/1508)) ([ac4fb88](https://github.com/ngrx/platform/commit/ac4fb88))
- **router-store:** add routerState to action payload ([#1511](https://github.com/ngrx/platform/issues/1511)) ([283424f](https://github.com/ngrx/platform/commit/283424f))
- **schematics:** add ng add support for [@ngrx](https://github.com/ngrx)/entity ([#1503](https://github.com/ngrx/platform/issues/1503)) ([da1c955](https://github.com/ngrx/platform/commit/da1c955))
- **schematics:** implement router store ng-add ([#1487](https://github.com/ngrx/platform/issues/1487)) ([9da4aac](https://github.com/ngrx/platform/commit/9da4aac)), closes [#1479](https://github.com/ngrx/platform/issues/1479)
- **store:** support store config factory for feature ([#1445](https://github.com/ngrx/platform/issues/1445)) ([6aa5645](https://github.com/ngrx/platform/commit/6aa5645)), closes [#1414](https://github.com/ngrx/platform/issues/1414)

<a name="7.0.0"></a>

# [7.0.0](https://github.com/ngrx/platform/compare/7.0.0-beta.1...7.0.0) (2018-12-20)

### Features

- **Effects:** add OnInitEffects interface to dispatch an action on initialization ([e921cd9](https://github.com/ngrx/platform/commit/e921cd9))
- **RouterStore:** make the router store key selector generic ([a30a514](https://github.com/ngrx/platform/commit/a30a514)), closes [#1457](https://github.com/ngrx/platform/issues/1457)
- **schematics:** add project flag support to specify apps or libs ([#1477](https://github.com/ngrx/platform/issues/1477)) ([af39fd2](https://github.com/ngrx/platform/commit/af39fd2)), closes [#1455](https://github.com/ngrx/platform/issues/1455)

### Reverts

- **Effects:** dispatch init feature effects action on init [#1305](https://github.com/ngrx/platform/issues/1305) ([e9cc9ae](https://github.com/ngrx/platform/commit/e9cc9ae))

<a name="7.0.0-beta.1"></a>

# [7.0.0-beta.1](https://github.com/ngrx/platform/compare/7.0.0-beta.0...7.0.0-beta.1) (2018-12-04)

### Features

- **effects:** add OnIdentifyEffects interface to register multiple effect instances ([#1448](https://github.com/ngrx/platform/issues/1448)) ([b553ce7](https://github.com/ngrx/platform/commit/b553ce7))
- **store-devtools:** catch and log redux devtools errors ([#1450](https://github.com/ngrx/platform/issues/1450)) ([4ed16cd](https://github.com/ngrx/platform/commit/4ed16cd))

<a name="7.0.0-beta.0"></a>

# [7.0.0-beta.0](https://github.com/ngrx/platform/compare/6.1.0...7.0.0-beta.0) (2018-11-03)

### Bug Fixes

- **docs-infra:** ARIA roles used must conform to valid values ([8a4b2de](https://github.com/ngrx/platform/commit/8a4b2de))
- **docs-infra:** elements must have sufficient color contrast ([c5dfaef](https://github.com/ngrx/platform/commit/c5dfaef))
- **docs-infra:** html element must have a lang attribute ([32256de](https://github.com/ngrx/platform/commit/32256de))
- **docs-infra:** Images must have alternate text ([8241f99](https://github.com/ngrx/platform/commit/8241f99))
- **docs-infra:** notification must have sufficient color contrast ([ac24cc3](https://github.com/ngrx/platform/commit/ac24cc3))
- **example:** close side nav when escape key is pressed ([#1244](https://github.com/ngrx/platform/issues/1244)) ([b3fc5dd](https://github.com/ngrx/platform/commit/b3fc5dd)), closes [#1172](https://github.com/ngrx/platform/issues/1172)
- **router-store:** Added new imports to index.ts, codestyle ([293f960](https://github.com/ngrx/platform/commit/293f960))
- **router-store:** allow compilation with strictFunctionTypes ([#1385](https://github.com/ngrx/platform/issues/1385)) ([0e38673](https://github.com/ngrx/platform/commit/0e38673)), closes [#1344](https://github.com/ngrx/platform/issues/1344)
- **router-store:** Avoiding [@ngrx](https://github.com/ngrx)/effects dependency inside tests ([11d3b9f](https://github.com/ngrx/platform/commit/11d3b9f))
- **router-store:** handle internal navigation error, dispatch cancel/error action with previous state ([#1294](https://github.com/ngrx/platform/issues/1294)) ([5300e7d](https://github.com/ngrx/platform/commit/5300e7d))
- **schematics:** correct spec description in reducer template ([#1269](https://github.com/ngrx/platform/issues/1269)) ([b7ab4f8](https://github.com/ngrx/platform/commit/b7ab4f8))
- **schematics:** fix effects code generated by schematics:feature ([#1357](https://github.com/ngrx/platform/issues/1357)) ([458e2b4](https://github.com/ngrx/platform/commit/458e2b4))
- **store:** add typing to allow props with store.select ([#1387](https://github.com/ngrx/platform/issues/1387)) ([a9e7cbd](https://github.com/ngrx/platform/commit/a9e7cbd))
- **store:** memoize selector arguments ([#1393](https://github.com/ngrx/platform/issues/1393)) ([7cc9702](https://github.com/ngrx/platform/commit/7cc9702)), closes [#1389](https://github.com/ngrx/platform/issues/1389)
- **store:** remove deprecation from Store.select ([#1382](https://github.com/ngrx/platform/issues/1382)) ([626784e](https://github.com/ngrx/platform/commit/626784e))

### Code Refactoring

- **routerstore:** change default state key to router ([#1258](https://github.com/ngrx/platform/issues/1258)) ([e8173d9](https://github.com/ngrx/platform/commit/e8173d9))
- **RouterStore:** normalize actions ([#1302](https://github.com/ngrx/platform/issues/1302)) ([466e2cd](https://github.com/ngrx/platform/commit/466e2cd))

### Features

- update angular dependencies to V7 ([e6048bd](https://github.com/ngrx/platform/commit/e6048bd)), closes [#1340](https://github.com/ngrx/platform/issues/1340)
- **effects:** add smarter type inference for ofType operator. ([#1183](https://github.com/ngrx/platform/issues/1183)) ([8d56a6f](https://github.com/ngrx/platform/commit/8d56a6f))
- **effects:** add support for effects of different instances of same class ([#1249](https://github.com/ngrx/platform/issues/1249)) ([518e561](https://github.com/ngrx/platform/commit/518e561)), closes [#1246](https://github.com/ngrx/platform/issues/1246)
- **effects:** dispatch feature effects action on init ([#1305](https://github.com/ngrx/platform/issues/1305)) ([15a4b58](https://github.com/ngrx/platform/commit/15a4b58)), closes [#683](https://github.com/ngrx/platform/issues/683)
- **entity:** add support for predicate to removeMany ([#900](https://github.com/ngrx/platform/issues/900)) ([d7daa2f](https://github.com/ngrx/platform/commit/d7daa2f))
- **entity:** add support for predicate to updateMany ([#907](https://github.com/ngrx/platform/issues/907)) ([4e4c50f](https://github.com/ngrx/platform/commit/4e4c50f))
- **example:** add logout confirmation ([#1287](https://github.com/ngrx/platform/issues/1287)) ([ba8d300](https://github.com/ngrx/platform/commit/ba8d300)), closes [#1271](https://github.com/ngrx/platform/issues/1271)
- **router-store:** Add custom serializer to config object ([5c814a9](https://github.com/ngrx/platform/commit/5c814a9)), closes [#1262](https://github.com/ngrx/platform/issues/1262)
- **router-store:** Add support for serializers with injected values ([959cfac](https://github.com/ngrx/platform/commit/959cfac))
- **router-store:** config option to dispatch ROUTER_NAVIGATION later ([fe71ffb](https://github.com/ngrx/platform/commit/fe71ffb)), closes [#1263](https://github.com/ngrx/platform/issues/1263)
- **router-store:** New router Actions ROUTER_REQUEST and ROUTER_NAVIGATED ([9f731c3](https://github.com/ngrx/platform/commit/9f731c3)), closes [#1010](https://github.com/ngrx/platform/issues/1010) [#1263](https://github.com/ngrx/platform/issues/1263)
- **router-store:** serialize routeConfig inside the default serializer ([#1384](https://github.com/ngrx/platform/issues/1384)) ([18a16d4](https://github.com/ngrx/platform/commit/18a16d4))
- **router-store:** update stateKey definition to take a string or selector ([4ad9a94](https://github.com/ngrx/platform/commit/4ad9a94)), closes [#1300](https://github.com/ngrx/platform/issues/1300)
- **store:** add testing package ([#1027](https://github.com/ngrx/platform/issues/1027)) ([ab56aac](https://github.com/ngrx/platform/commit/ab56aac)), closes [#915](https://github.com/ngrx/platform/issues/915)
- **store:** dispatch one update action when features are added or removed ([#1240](https://github.com/ngrx/platform/issues/1240)) ([0b90f91](https://github.com/ngrx/platform/commit/0b90f91))
- **Store:** export SelectorWithProps and MemoizedSelectorWithProps ([#1341](https://github.com/ngrx/platform/issues/1341)) ([df8fc60](https://github.com/ngrx/platform/commit/df8fc60))
- **store-devtools:** add support for persist, lock, pause ([#955](https://github.com/ngrx/platform/issues/955)) ([93fcf56](https://github.com/ngrx/platform/commit/93fcf56)), closes [#853](https://github.com/ngrx/platform/issues/853) [#919](https://github.com/ngrx/platform/issues/919)
- **store-devtools:** use different action when recomputing state history ([#1353](https://github.com/ngrx/platform/issues/1353)) ([1448a0e](https://github.com/ngrx/platform/commit/1448a0e)), closes [#1255](https://github.com/ngrx/platform/issues/1255)
- **StoreDevtools:** implement actionsBlacklist/Whitelist & predicate ([#970](https://github.com/ngrx/platform/issues/970)) ([7ee46d2](https://github.com/ngrx/platform/commit/7ee46d2)), closes [#938](https://github.com/ngrx/platform/issues/938)

### BREAKING CHANGES

- **router-store:** The default router serializer now returns a `null` value for
  `routeConfig` when `routeConfig` doesn't exist on the
  `ActivatedRouteSnapshot` instead of an empty object.

BEFORE:

```json
{
  "routeConfig": {}
}
```

AFTER:

```json
{
  "routeConfig": null
}
```

- **effects:** Removes .ofType method on Actions. Instead use the provided 'ofType'
  rxjs operator.

BEFORE:

```ts
this.actions.ofType('INCREMENT');
```

AFTER:

```ts
import { ofType } from '@ngrx/store';
...
this.action.pipe(ofType('INCREMENT'))
```

- **RouterStore:** Normalize router store actions to be consistent with the other modules

BEFORE:

- ROUTER_REQUEST
- ROUTER_NAVIGATION
- ROUTER_CANCEL
- ROUTER_ERROR
- ROUTER_NAVIGATED

AFTER

- @ngrx/router-store/request
- @ngrx/router-store/navigation
- @ngrx/router-store/cancel
- @ngrx/router-store/error
- @ngrx/router-store/navigated

* **router-store:** StoreRouterConfigFunction is removed. It is no longer possible to pass a function returning a StoreRouterConfig to StoreRouterConnectingModule.forRoot

If you still need this, pass a provider like this:
{
provide: ROUTER_CONFIG,
useFactory: \_createRouterConfig // you function
}

- **routerstore:** The default state key is changed from routerReducer to router
- **store:** BEFORE:

```ts
{type: '@ngrx/store/update-reducers', feature: 'feature1'}
{type: '@ngrx/store/update-reducers', feature: 'feature2'}
```

AFTER:

```ts
{type: '@ngrx/store/update-reducers', features: ['feature1',
'feature2']}
```

<a name="6.1.0"></a>

# [6.1.0](https://github.com/ngrx/platform/compare/6.0.1...6.1.0) (2018-08-02)

### Bug Fixes

- **effects:** Add deprecation notice for ofType instance operator ([830c8fa](https://github.com/ngrx/platform/commit/830c8fa))
- **Effects:** Added defaults for ng-add schematic ([9d36016](https://github.com/ngrx/platform/commit/9d36016))
- **example:** adjust styles to display spinner correctly ([#1203](https://github.com/ngrx/platform/issues/1203)) ([4a0b580](https://github.com/ngrx/platform/commit/4a0b580))
- **example:** remove custom router state serializer ([#1129](https://github.com/ngrx/platform/issues/1129)) ([389cd78](https://github.com/ngrx/platform/commit/389cd78))
- **schematics:** correct a type of action class generated ([#1140](https://github.com/ngrx/platform/issues/1140)) ([bbb7e8c](https://github.com/ngrx/platform/commit/bbb7e8c))
- **schematics:** exclude environment imports for libraries ([#1213](https://github.com/ngrx/platform/issues/1213)) ([541de02](https://github.com/ngrx/platform/commit/541de02)), closes [#1205](https://github.com/ngrx/platform/issues/1205) [#1197](https://github.com/ngrx/platform/issues/1197)
- **schematics:** Remove peer dependencies on Angular DevKit ([#1222](https://github.com/ngrx/platform/issues/1222)) ([fd3da16](https://github.com/ngrx/platform/commit/fd3da16)), closes [#1206](https://github.com/ngrx/platform/issues/1206)
- **Schematics:** correct resolution of environments path for module ([#1094](https://github.com/ngrx/platform/issues/1094)) ([d24ed10](https://github.com/ngrx/platform/commit/d24ed10)), closes [#1090](https://github.com/ngrx/platform/issues/1090)
- **store:** Add deprecation notice for select instance operator ([232ca7a](https://github.com/ngrx/platform/commit/232ca7a))
- **store:** Compare results in addition to arguments change in memoizer ([#1175](https://github.com/ngrx/platform/issues/1175)) ([99e1313](https://github.com/ngrx/platform/commit/99e1313))
- **Store:** bootstrap store with partial initial state ([#1163](https://github.com/ngrx/platform/issues/1163)) ([11bd465](https://github.com/ngrx/platform/commit/11bd465)), closes [#906](https://github.com/ngrx/platform/issues/906) [#909](https://github.com/ngrx/platform/issues/909)
- **Store:** Fix import bug with ng-add and added defaults ([ff7dc72](https://github.com/ngrx/platform/commit/ff7dc72))

### Features

- **effects:** stringify action when reporting as invalid ([#1219](https://github.com/ngrx/platform/issues/1219)) ([73d32eb](https://github.com/ngrx/platform/commit/73d32eb))
- **entity:** log a warning message when selectId returns undefined in dev mode ([#1169](https://github.com/ngrx/platform/issues/1169)) ([8f05f1f](https://github.com/ngrx/platform/commit/8f05f1f)), closes [#1133](https://github.com/ngrx/platform/issues/1133)
- **Entity:** expose Dictionary as part of the public API ([#1118](https://github.com/ngrx/platform/issues/1118)) ([2a267b6](https://github.com/ngrx/platform/commit/2a267b6)), closes [#865](https://github.com/ngrx/platform/issues/865)
- **schematics:** display provided path when displaying an error ([#1208](https://github.com/ngrx/platform/issues/1208)) ([91cc6ed](https://github.com/ngrx/platform/commit/91cc6ed)), closes [#1200](https://github.com/ngrx/platform/issues/1200)
- **schematics:** use ofType operator function instead of Actions#ofType ([#1154](https://github.com/ngrx/platform/issues/1154)) ([cb58ff1](https://github.com/ngrx/platform/commit/cb58ff1))
- **store:** add an overload to createFeatureSelector to provide better type checking ([#1171](https://github.com/ngrx/platform/issues/1171)) ([03db76f](https://github.com/ngrx/platform/commit/03db76f)), closes [#1136](https://github.com/ngrx/platform/issues/1136)
- **store:** provide props to createSelector projector function ([#1210](https://github.com/ngrx/platform/issues/1210)) ([b1f9b34](https://github.com/ngrx/platform/commit/b1f9b34))
- **Store:** createSelector allow props in selector ([53832a1](https://github.com/ngrx/platform/commit/53832a1))
- **Store:** createSelector with only a props selector ([35a4848](https://github.com/ngrx/platform/commit/35a4848))
- **StoreDevtools:** Add ng-add support ([be28d8d](https://github.com/ngrx/platform/commit/be28d8d))
- **StoreDevtools:** Allow custom serializer options ([#1121](https://github.com/ngrx/platform/issues/1121)) ([55a0488](https://github.com/ngrx/platform/commit/55a0488))

### Performance Improvements

- **Effects:** remove path filters in ng-add ([5318913](https://github.com/ngrx/platform/commit/5318913))
- **Schematics:** remove path filters in effects schematics ([6d3f5a1](https://github.com/ngrx/platform/commit/6d3f5a1))
- **Schematics:** remove path filters in reducer schematics ([055f6ef](https://github.com/ngrx/platform/commit/055f6ef))
- **Schematics:** remove path filters in store schematics ([762cf2e](https://github.com/ngrx/platform/commit/762cf2e))
- **Store:** remove path filters in ng-add ([ec6adb5](https://github.com/ngrx/platform/commit/ec6adb5))
- **StoreDevtools:** remove path filters in ng-add ([3ba463f](https://github.com/ngrx/platform/commit/3ba463f))

<a name="6.0.1"></a>

## [6.0.1](https://github.com/ngrx/platform/compare/6.0.0...6.0.1) (2018-05-23)

<a name="6.0.0"></a>

# [6.0.0](https://github.com/ngrx/platform/compare/v6.0.0-beta.3...6.0.0) (2018-05-23)

### Bug Fixes

- **Schematics:** remove ts extension when importing reducer in container ([#1061](https://github.com/ngrx/platform/issues/1061)) ([d1ed9e5](https://github.com/ngrx/platform/commit/d1ed9e5)), closes [#1056](https://github.com/ngrx/platform/issues/1056)
- **Schematics:** Update parsed path logic to split path and name ([a1e9530](https://github.com/ngrx/platform/commit/a1e9530)), closes [#1064](https://github.com/ngrx/platform/issues/1064)
- **Store:** Resolve environment path when generating a new store ([#1071](https://github.com/ngrx/platform/issues/1071)) ([599cfb6](https://github.com/ngrx/platform/commit/599cfb6))

### Features

- implement ng add for store and effects packages ([db94db7](https://github.com/ngrx/platform/commit/db94db7))

<a name="6.0.0-beta.3"></a>

# [6.0.0-beta.3](https://github.com/ngrx/platform/compare/v6.0.0-beta.2...v6.0.0-beta.3) (2018-05-12)

### Bug Fixes

- **build:** Use default build for schematics ([#1057](https://github.com/ngrx/platform/issues/1057)) ([355b12f](https://github.com/ngrx/platform/commit/355b12f))

<a name="6.0.0-beta.2"></a>

# [6.0.0-beta.2](https://github.com/ngrx/platform/compare/v6.0.0-beta.1...v6.0.0-beta.2) (2018-05-11)

### Bug Fixes

- **build:** Fix UMD global names ([#1005](https://github.com/ngrx/platform/issues/1005)) ([413efd4](https://github.com/ngrx/platform/commit/413efd4)), closes [#1004](https://github.com/ngrx/platform/issues/1004)
- **RouterStore:** Reset dispatch-tracking booleans after navigation end ([#968](https://github.com/ngrx/platform/issues/968)) ([48305aa](https://github.com/ngrx/platform/commit/48305aa))
- **Schematics:** Add check for app/lib to project helper function ([5942885](https://github.com/ngrx/platform/commit/5942885))
- **Schematics:** Add smart default to blueprint schemas ([cdd247e](https://github.com/ngrx/platform/commit/cdd247e))
- **Schematics:** Remove aliases for state and stateInterface options ([f4520a2](https://github.com/ngrx/platform/commit/f4520a2))
- **Schematics:** Update upsert actions for entity blueprint ([#1042](https://github.com/ngrx/platform/issues/1042)) ([0d1d309](https://github.com/ngrx/platform/commit/0d1d309)), closes [#1039](https://github.com/ngrx/platform/issues/1039)
- **Schematics:** Upgrade schematics to new CLI structure ([b99d9ff](https://github.com/ngrx/platform/commit/b99d9ff))
- **Store:** Fix type annotations for select methods ([#953](https://github.com/ngrx/platform/issues/953)) ([4d74bd2](https://github.com/ngrx/platform/commit/4d74bd2))
- **StoreDevtools:** Refresh devtools when extension is started ([#1017](https://github.com/ngrx/platform/issues/1017)) ([c6e33d9](https://github.com/ngrx/platform/commit/c6e33d9)), closes [#508](https://github.com/ngrx/platform/issues/508)
- Update minimum node version to 8.9.0 ([#989](https://github.com/ngrx/platform/issues/989)) ([0baaad8](https://github.com/ngrx/platform/commit/0baaad8))

### Features

- Add ng update support to ngrx packages ([#1053](https://github.com/ngrx/platform/issues/1053)) ([4f91e9e](https://github.com/ngrx/platform/commit/4f91e9e))
- **Schematics:** Rename default action type for action blueprint ([#1047](https://github.com/ngrx/platform/issues/1047)) ([4c4e6a9](https://github.com/ngrx/platform/commit/4c4e6a9)), closes [#1040](https://github.com/ngrx/platform/issues/1040)
- **Store:** Add support ng update ([#1032](https://github.com/ngrx/platform/issues/1032)) ([5b4f067](https://github.com/ngrx/platform/commit/5b4f067))

### BREAKING CHANGES

- **Schematics:** The action blueprint has been updated to be less generic, with associated reducer and effects updated for the feature blueprint

BEFORE:

export enum UserActionTypes {
UserAction = '[User] Action'
}

export class User implements Action {
readonly type = UserActionTypes.UserAction;
}

export type UserActions = User;

AFTER:

export enum UserActionTypes {
LoadUsers = '[User] Load Users'
}

export class LoadUsers implements Action {
readonly type = UserActionTypes.LoadUsers;
}

export type UserActions = LoadUsers;

- **Schematics:** Aliases for `state` and `stateInterface` were removed due to conflicts with component aliases without reasonable alternatives.
- **Schematics:** Minimum dependency for @ngrx/schematics has changed:

@angular-devkit/core: ^0.5.0
@angular-devkit/schematics: ^0.5.0

<a name="6.0.0-beta.1"></a>

# [6.0.0-beta.1](https://github.com/ngrx/platform/compare/v6.0.0-beta.0...v6.0.0-beta.1) (2018-04-02)

### Bug Fixes

- Declare global NgRx packages for UMD bundles ([#952](https://github.com/ngrx/platform/issues/952)) ([ba2139d](https://github.com/ngrx/platform/commit/ba2139d)), closes [#949](https://github.com/ngrx/platform/issues/949)

<a name="6.0.0-beta.0"></a>

# [6.0.0-beta.0](https://github.com/ngrx/platform/compare/v5.2.0...v6.0.0-beta.0) (2018-03-31)

### Bug Fixes

- **Entity:** Change EntityAdapter upsertOne/upsertMany to accept an entity ([a0f45ff](https://github.com/ngrx/platform/commit/a0f45ff))
- **RouterStore:** Allow strict mode with router reducer ([#903](https://github.com/ngrx/platform/issues/903)) ([f17a032](https://github.com/ngrx/platform/commit/f17a032))
- **RouterStore:** change the default serializer to work around cycles in RouterStateSnapshot ([7917a27](https://github.com/ngrx/platform/commit/7917a27))
- **RouterStore:** Replace RouterStateSnapshot with SerializedRouterStateSnapshot ([bd415a1](https://github.com/ngrx/platform/commit/bd415a1))
- **StoreDevtools:** pass timestamp to actions ([df2411f](https://github.com/ngrx/platform/commit/df2411f))
- **StoreDevtools:** report errors to ErrorHandler instead of console ([32df3f0](https://github.com/ngrx/platform/commit/32df3f0))
- Add support for Angular 6 and RxJS 6 ([d1286d2](https://github.com/ngrx/platform/commit/d1286d2))

### Features

- **Schematcis:** Extend from [@schematics](https://github.com/schematics)/angular ([0e17aad](https://github.com/ngrx/platform/commit/0e17aad))
- **Schematics:** Add support for custom store interface name ([#810](https://github.com/ngrx/platform/issues/810)) ([1352d83](https://github.com/ngrx/platform/commit/1352d83))

### BREAKING CHANGES

- **StoreDevtools:** Errors in reducers are no longer hidden from ErrorHandler by
  StoreDevtools

BEFORE:

Errors in reducers are caught by StoreDevtools and logged to the console

AFTER:

Errors in reducers are reported to ErrorHandler

- **Schematcis:** NgRx Schematics now has a minimum version dependency on @angular-devkit/core
  and @angular-devkit/schematics of v0.4.0.
- **RouterStore:** Default router state is serialized to a shape that removes cycles

BEFORE:

Full RouterStateSnapshot is returned

AFTER:

Router state snapshot is returned as a SerializedRouterStateSnapshot with cyclical dependencies removed

- **Entity:** The signature of the upsertOne/upsertMany functions in the EntityAdapter
  has been changed to accept a fully qualified entity instead of an update
  object that implements the Update<T> interface.

  Before:

  ```ts
  entityAdapter.upsertOne(
    {
      id: 'Entity ID',
      changes: { id: 'Entity ID', name: 'Entity Name' },
    },
    state
  );
  ```

  After:

  ```ts
  entityAdapter.upsertOne(
    {
      id: 'Entity ID',
      name: 'Entity Name',
    },
    state
  );
  ```

- NgRx now has a minimum version requirement on Angular 6 and RxJS 6.

<a name="5.2.0"></a>

# [5.2.0](https://github.com/ngrx/platform/compare/v5.1.0...v5.2.0) (2018-03-07)

### Bug Fixes

- **Schematics:** Correct usage of upsert actions for entity blueprint ([#821](https://github.com/ngrx/platform/issues/821)) ([1ffb5a9](https://github.com/ngrx/platform/commit/1ffb5a9))
- **Store:** only default to initialValue when store value is undefined ([#886](https://github.com/ngrx/platform/issues/886)) ([51a1547](https://github.com/ngrx/platform/commit/51a1547))
- **StoreDevtools:** Fix bug when exporting/importing state history ([#855](https://github.com/ngrx/platform/issues/855)) ([a5dcdb1](https://github.com/ngrx/platform/commit/a5dcdb1))
- **StoreDevtools:** Recompute state history when reducers are updated ([#844](https://github.com/ngrx/platform/issues/844)) ([10debcc](https://github.com/ngrx/platform/commit/10debcc))

### Features

- **Entity:** Add 'selectId' and 'sortComparer' to state adapter ([#889](https://github.com/ngrx/platform/issues/889)) ([69a62f2](https://github.com/ngrx/platform/commit/69a62f2))
- **Store:** Added feature name to Update Reducers action ([730361e](https://github.com/ngrx/platform/commit/730361e))

<a name="5.1.0"></a>

# [5.1.0](https://github.com/ngrx/platform/compare/v5.0.1...v5.1.0) (2018-02-13)

### Bug Fixes

- **Devtools:** Ensure Store is loaded eagerly ([#801](https://github.com/ngrx/platform/issues/801)) ([ecf1ebf](https://github.com/ngrx/platform/commit/ecf1ebf)), closes [#624](https://github.com/ngrx/platform/issues/624) [#741](https://github.com/ngrx/platform/issues/741)
- **Effects:** Make ofType operator strictFunctionTypes safe ([#789](https://github.com/ngrx/platform/issues/789)) ([c8560e4](https://github.com/ngrx/platform/commit/c8560e4)), closes [#753](https://github.com/ngrx/platform/issues/753)
- **Entity:** Avoid for..in iteration in sorted state adapter ([#805](https://github.com/ngrx/platform/issues/805)) ([4192645](https://github.com/ngrx/platform/commit/4192645))
- **Entity:** Do not add Array.prototype properties to store ([#782](https://github.com/ngrx/platform/issues/782)) ([d537758](https://github.com/ngrx/platform/commit/d537758)), closes [#781](https://github.com/ngrx/platform/issues/781)
- **Entity:** Properly iterate over array in upsert ([#802](https://github.com/ngrx/platform/issues/802)) ([779d689](https://github.com/ngrx/platform/commit/779d689))
- **Schematics:** Add store import to container blueprint ([#763](https://github.com/ngrx/platform/issues/763)) ([a140fa9](https://github.com/ngrx/platform/commit/a140fa9)), closes [#760](https://github.com/ngrx/platform/issues/760)
- **Schematics:** Remove extra braces from constructor for container blueprint ([#791](https://github.com/ngrx/platform/issues/791)) ([945bf40](https://github.com/ngrx/platform/commit/945bf40)), closes [#778](https://github.com/ngrx/platform/issues/778)
- **Schematics:** Use correct paths for nested and grouped feature blueprint ([#756](https://github.com/ngrx/platform/issues/756)) ([c219770](https://github.com/ngrx/platform/commit/c219770))
- **StoreDevtools:** Add internal support for ActionSanitizer and StateSanitizer ([#795](https://github.com/ngrx/platform/issues/795)) ([a7de2a6](https://github.com/ngrx/platform/commit/a7de2a6))
- **StoreDevtools:** Do not send full liftedState for application actions ([#790](https://github.com/ngrx/platform/issues/790)) ([c11504f](https://github.com/ngrx/platform/commit/c11504f))

### Features

- **Entity:** Add upsertOne and upsertMany functions to entity adapters ([#780](https://github.com/ngrx/platform/issues/780)) ([f871540](https://github.com/ngrx/platform/commit/f871540)), closes [#421](https://github.com/ngrx/platform/issues/421)
- **Schematics:** Add group option to entity blueprint ([#792](https://github.com/ngrx/platform/issues/792)) ([0429276](https://github.com/ngrx/platform/commit/0429276)), closes [#779](https://github.com/ngrx/platform/issues/779)
- **Schematics:** Add upsert methods to entity blueprint ([#809](https://github.com/ngrx/platform/issues/809)) ([7acdc79](https://github.com/ngrx/platform/commit/7acdc79)), closes [#592](https://github.com/ngrx/platform/issues/592)

<a name="5.0.1"></a>

## [5.0.1](https://github.com/ngrx/platform/compare/v5.0.0...v5.0.1) (2018-01-25)

### Bug Fixes

- **Effects:** Provide instance from actions to ofType lettable operator ([#751](https://github.com/ngrx/platform/issues/751)) ([33d48e7](https://github.com/ngrx/platform/commit/33d48e7)), closes [#739](https://github.com/ngrx/platform/issues/739)

<a name="5.0.0"></a>

# [5.0.0](https://github.com/ngrx/platform/compare/v4.1.1...v5.0.0) (2018-01-22)

### Bug Fixes

- **Effects:** Ensure Store modules are loaded eagerly ([#658](https://github.com/ngrx/platform/issues/658)) ([0a3398d](https://github.com/ngrx/platform/commit/0a3398d)), closes [#642](https://github.com/ngrx/platform/issues/642)
- **Effects:** Remove toPayload utility function ([#738](https://github.com/ngrx/platform/issues/738)) ([b390ef5](https://github.com/ngrx/platform/commit/b390ef5))
- **Entity:** updateOne/updateMany should not change ids state on existing entity ([#581](https://github.com/ngrx/platform/issues/581)) ([b989e4b](https://github.com/ngrx/platform/commit/b989e4b)), closes [#571](https://github.com/ngrx/platform/issues/571)
- **RouterStore:** Fix usage of config object if provided ([#575](https://github.com/ngrx/platform/issues/575)) ([4125914](https://github.com/ngrx/platform/commit/4125914))
- **RouterStore:** Match RouterAction type parameters ([#562](https://github.com/ngrx/platform/issues/562)) ([980a653](https://github.com/ngrx/platform/commit/980a653))
- **Schematics:** Add group folder after feature name folder ([#737](https://github.com/ngrx/platform/issues/737)) ([317fb94](https://github.com/ngrx/platform/commit/317fb94))
- **Schematics:** Add handling of flat option to entity blueprint ([fb8d2c6](https://github.com/ngrx/platform/commit/fb8d2c6))
- **Schematics:** Distinguish between root and feature effect arrays when registering ([#718](https://github.com/ngrx/platform/issues/718)) ([95ff6c8](https://github.com/ngrx/platform/commit/95ff6c8))
- **Schematics:** Don't add state import if not provided ([#697](https://github.com/ngrx/platform/issues/697)) ([e5c2aed](https://github.com/ngrx/platform/commit/e5c2aed))
- **Schematics:** Make variable naming consistent for entity blueprint ([#716](https://github.com/ngrx/platform/issues/716)) ([765b15a](https://github.com/ngrx/platform/commit/765b15a))
- **Store:** Compose provided metareducers for a feature reducer ([#704](https://github.com/ngrx/platform/issues/704)) ([1454620](https://github.com/ngrx/platform/commit/1454620)), closes [#701](https://github.com/ngrx/platform/issues/701)
- **StoreDevtools:** Only recompute current state when reducers are updated ([#570](https://github.com/ngrx/platform/issues/570)) ([247ae1a](https://github.com/ngrx/platform/commit/247ae1a)), closes [#229](https://github.com/ngrx/platform/issues/229) [#487](https://github.com/ngrx/platform/issues/487)
- **typo:** update login error to use correct css font color property ([41723fc](https://github.com/ngrx/platform/commit/41723fc))

### Features

- **Effects:** Add lettable ofType operator ([d5e1814](https://github.com/ngrx/platform/commit/d5e1814))
- **ErrorHandler:** Use the Angular ErrorHandler for reporting errors ([#667](https://github.com/ngrx/platform/issues/667)) ([8f297d1](https://github.com/ngrx/platform/commit/8f297d1)), closes [#626](https://github.com/ngrx/platform/issues/626)
- **material:** Upgrade [@angular](https://github.com/angular)/material to v 2.0.0-beta.12 ([#482](https://github.com/ngrx/platform/issues/482)) ([aedf20e](https://github.com/ngrx/platform/commit/aedf20e)), closes [#448](https://github.com/ngrx/platform/issues/448)
- **Schematics:** Add alias for container, store and action blueprints ([#685](https://github.com/ngrx/platform/issues/685)) ([dc64ac9](https://github.com/ngrx/platform/commit/dc64ac9))
- **Schematics:** Add alias for reducer blueprint ([#684](https://github.com/ngrx/platform/issues/684)) ([ea98fb7](https://github.com/ngrx/platform/commit/ea98fb7))
- **Schematics:** Add effect to registered effects array ([#717](https://github.com/ngrx/platform/issues/717)) ([f1082fe](https://github.com/ngrx/platform/commit/f1082fe))
- **Schematics:** Add option to group feature blueprints in respective folders ([#736](https://github.com/ngrx/platform/issues/736)) ([b82c35d](https://github.com/ngrx/platform/commit/b82c35d))
- **Schematics:** Introduce [@ngrx](https://github.com/ngrx)/schematics ([#631](https://github.com/ngrx/platform/issues/631)) ([1837dba](https://github.com/ngrx/platform/commit/1837dba)), closes [#53](https://github.com/ngrx/platform/issues/53)
- **Store:** Add lettable select operator ([77eed24](https://github.com/ngrx/platform/commit/77eed24))
- **Store:** Add support for generating custom createSelector functions ([#734](https://github.com/ngrx/platform/issues/734)) ([cb0d185](https://github.com/ngrx/platform/commit/cb0d185)), closes [#478](https://github.com/ngrx/platform/issues/478) [#724](https://github.com/ngrx/platform/issues/724)
- **StoreDevtools:** Add option to configure extension in log-only mode ([#712](https://github.com/ngrx/platform/issues/712)) ([1ecd658](https://github.com/ngrx/platform/commit/1ecd658)), closes [#643](https://github.com/ngrx/platform/issues/643) [#374](https://github.com/ngrx/platform/issues/374)
- **StoreDevtools:** Add support for custom instance name ([#517](https://github.com/ngrx/platform/issues/517)) ([00be3d1](https://github.com/ngrx/platform/commit/00be3d1)), closes [#463](https://github.com/ngrx/platform/issues/463)
- **StoreDevtools:** Add support for extension sanitizers ([#544](https://github.com/ngrx/platform/issues/544)) ([6ed92b0](https://github.com/ngrx/platform/commit/6ed92b0)), closes [#494](https://github.com/ngrx/platform/issues/494)
- **StoreDevtools:** Add support for jumping to a specific action ([#703](https://github.com/ngrx/platform/issues/703)) ([b9f6442](https://github.com/ngrx/platform/commit/b9f6442)), closes [#681](https://github.com/ngrx/platform/issues/681)

### BREAKING CHANGES

- **Effects:** The utility function `toPayload`, deprecated in @ngrx/effects v4.0, has been removed.

  Before:

  ```ts
  import { toPayload } from '@ngrx/effects';

  actions$.ofType('SOME_ACTION').map(toPayload);
  ```

  After:

  ```ts
  actions$
    .ofType('SOME_ACTION')
    .map((action: SomeActionWithPayload) => action.payload);
  ```

- **ErrorHandler:** The ErrorReporter has been replaced with ErrorHandler
  from angular/core.

BEFORE:

Errors were reported to the ngrx/effects ErrorReporter. The
ErrorReporter would log to the console by default.

AFTER:

Errors are now reported to the @angular/core ErrorHandler.

- **Store:** Updates minimum version of RxJS dependency.

BEFORE:

Minimum peer dependency of RxJS ^5.0.0

AFTER:

Minimum peer dependency of RxJS ^5.5.0

- **Effects:** Updates minimum version of RxJS dependency.

BEFORE:

Minimum peer dependency of RxJS ^5.0.0

AFTER:

Minimum peer dependency of RxJS ^5.5.0

<a name="4.1.1"></a>

## [4.1.1](https://github.com/ngrx/platform/compare/v4.1.0...v4.1.1) (2017-11-07)

### Bug Fixes

- Add support for Angular 5 ([30a8c56](https://github.com/ngrx/platform/commit/30a8c56))
- **Entity:** Fix type error for id selectors ([#533](https://github.com/ngrx/platform/issues/533)) ([88f672c](https://github.com/ngrx/platform/commit/88f672c)), closes [#525](https://github.com/ngrx/platform/issues/525)

### Features

- **Codegen:** Add base code and build for [@ngrx](https://github.com/ngrx)/codegen ([#534](https://github.com/ngrx/platform/issues/534)) ([2a22211](https://github.com/ngrx/platform/commit/2a22211))
- **RouterStore:** Add configurable option for router reducer name ([#417](https://github.com/ngrx/platform/issues/417)) ([ab7de5c](https://github.com/ngrx/platform/commit/ab7de5c)), closes [#410](https://github.com/ngrx/platform/issues/410)

<a name="4.1.0"></a>

# [4.1.0](https://github.com/ngrx/platform/compare/v4.0.5...v4.1.0) (2017-10-19)

### Bug Fixes

- **Build:** Fix build with space in path ([#331](https://github.com/ngrx/platform/issues/331)) ([257fc9d](https://github.com/ngrx/platform/commit/257fc9d))
- **combineSelectors:** Remove default parameter from function signature for Closure ([ae7d5e1](https://github.com/ngrx/platform/commit/ae7d5e1))
- **decorator:** add ExportDecoratedItems jsdoc for g3 ([#456](https://github.com/ngrx/platform/issues/456)) ([2b0e0cf](https://github.com/ngrx/platform/commit/2b0e0cf))
- **Effects:** Simplify decorator handling for Closure compatibility ([ad30d40](https://github.com/ngrx/platform/commit/ad30d40))
- **Entity:** Change type for EntityState to interface ([#454](https://github.com/ngrx/platform/issues/454)) ([d5640ec](https://github.com/ngrx/platform/commit/d5640ec)), closes [#458](https://github.com/ngrx/platform/issues/458)
- **Example:** Add missing import for catch operator ([#409](https://github.com/ngrx/platform/issues/409)) ([193e8b3](https://github.com/ngrx/platform/commit/193e8b3))
- **RouterStore:** Fix cancelled navigation with async guard (fixes [#354](https://github.com/ngrx/platform/issues/354)) ([#355](https://github.com/ngrx/platform/issues/355)) ([920c0ba](https://github.com/ngrx/platform/commit/920c0ba)), closes [#201](https://github.com/ngrx/platform/issues/201)
- **RouterStore:** Stringify error from navigation error event ([#357](https://github.com/ngrx/platform/issues/357)) ([0528d2d](https://github.com/ngrx/platform/commit/0528d2d)), closes [#356](https://github.com/ngrx/platform/issues/356)
- **Store:** Fix typing for feature to accept InjectionToken ([#375](https://github.com/ngrx/platform/issues/375)) ([38b2f95](https://github.com/ngrx/platform/commit/38b2f95))
- **Store:** Refactor parameter initialization in combineReducers for Closure ([5c60cba](https://github.com/ngrx/platform/commit/5c60cba))
- **Store:** Set initial value for state action pair to object ([#480](https://github.com/ngrx/platform/issues/480)) ([100a8ef](https://github.com/ngrx/platform/commit/100a8ef)), closes [#477](https://github.com/ngrx/platform/issues/477)

### Features

- **createSelector:** Expose projector function on selectors to improve testability ([56cb21f](https://github.com/ngrx/platform/commit/56cb21f)), closes [#290](https://github.com/ngrx/platform/issues/290)
- **Effects:** Add getEffectsMetadata() helper for verifying metadata ([628b865](https://github.com/ngrx/platform/commit/628b865)), closes [#491](https://github.com/ngrx/platform/issues/491)
- **Effects:** Add root effects init action ([#473](https://github.com/ngrx/platform/issues/473)) ([838ba17](https://github.com/ngrx/platform/commit/838ba17)), closes [#246](https://github.com/ngrx/platform/issues/246)
- **Entity:** Add default selectId function for EntityAdapter ([#405](https://github.com/ngrx/platform/issues/405)) ([2afb792](https://github.com/ngrx/platform/commit/2afb792))
- **Entity:** Add support for string or number type for ID ([#441](https://github.com/ngrx/platform/issues/441)) ([46d6f2f](https://github.com/ngrx/platform/commit/46d6f2f))
- **Entity:** Enable creating entity selectors without composing a state selector ([#490](https://github.com/ngrx/platform/issues/490)) ([aae4064](https://github.com/ngrx/platform/commit/aae4064))
- **Entity:** Rename 'sort' to 'sortComparer' ([274554b](https://github.com/ngrx/platform/commit/274554b)), closes [#370](https://github.com/ngrx/platform/issues/370)
- **Store:** createSelector with an array of selectors ([#340](https://github.com/ngrx/platform/issues/340)) ([2f6a035](https://github.com/ngrx/platform/commit/2f6a035)), closes [#192](https://github.com/ngrx/platform/issues/192)

<a name="4.0.5"></a>

## [4.0.5](https://github.com/ngrx/platform/compare/v4.0.4...v4.0.5) (2017-08-18)

### Bug Fixes

- **Effects:** Do not complete effects if one source errors or completes ([#297](https://github.com/ngrx/platform/issues/297)) ([54747cf](https://github.com/ngrx/platform/commit/54747cf)), closes [#232](https://github.com/ngrx/platform/issues/232)
- **Entity:** Return a referentially equal state if state did not change ([fbd6a66](https://github.com/ngrx/platform/commit/fbd6a66))
- **Entity:** Simplify target index finder for sorted entities ([335d255](https://github.com/ngrx/platform/commit/335d255))

<a name="4.0.4"></a>

## [4.0.4](https://github.com/ngrx/platform/compare/v4.0.3...v4.0.4) (2017-08-17)

### Bug Fixes

- **Effects:** Use factory provide for console ([#288](https://github.com/ngrx/platform/issues/288)) ([bf7f70c](https://github.com/ngrx/platform/commit/bf7f70c)), closes [#276](https://github.com/ngrx/platform/issues/276)
- **RouterStore:** Add generic type to RouterReducerState ([#292](https://github.com/ngrx/platform/issues/292)) ([6da3ec5](https://github.com/ngrx/platform/commit/6da3ec5)), closes [#289](https://github.com/ngrx/platform/issues/289)
- **RouterStore:** Only serialize snapshot in preactivation hook ([#287](https://github.com/ngrx/platform/issues/287)) ([bbb7c99](https://github.com/ngrx/platform/commit/bbb7c99)), closes [#286](https://github.com/ngrx/platform/issues/286)

<a name="4.0.3"></a>

## [4.0.3](https://github.com/ngrx/platform/compare/v4.0.2...v4.0.3) (2017-08-16)

### Bug Fixes

- **Effects:** Deprecate toPayload utility function ([#266](https://github.com/ngrx/platform/issues/266)) ([1cbb2c9](https://github.com/ngrx/platform/commit/1cbb2c9))
- **Effects:** Ensure StoreModule is loaded before effects ([#230](https://github.com/ngrx/platform/issues/230)) ([065d33e](https://github.com/ngrx/platform/commit/065d33e)), closes [#184](https://github.com/ngrx/platform/issues/184) [#219](https://github.com/ngrx/platform/issues/219)
- **Effects:** Export EffectsNotification interface ([#231](https://github.com/ngrx/platform/issues/231)) ([2b1a076](https://github.com/ngrx/platform/commit/2b1a076))
- **Store:** Add type signature for metareducer ([#270](https://github.com/ngrx/platform/issues/270)) ([57633d2](https://github.com/ngrx/platform/commit/57633d2)), closes [#264](https://github.com/ngrx/platform/issues/264) [#170](https://github.com/ngrx/platform/issues/170)
- **Store:** Set initial state for feature modules ([#235](https://github.com/ngrx/platform/issues/235)) ([4aec80c](https://github.com/ngrx/platform/commit/4aec80c)), closes [#206](https://github.com/ngrx/platform/issues/206) [#233](https://github.com/ngrx/platform/issues/233)
- **Store:** Update usage of compose for reducer factory ([#252](https://github.com/ngrx/platform/issues/252)) ([683013c](https://github.com/ngrx/platform/commit/683013c)), closes [#247](https://github.com/ngrx/platform/issues/247)
- **Store:** Use existing reducers when providing reducers without an InjectionToken ([#254](https://github.com/ngrx/platform/issues/254)) ([c409252](https://github.com/ngrx/platform/commit/c409252)), closes [#250](https://github.com/ngrx/platform/issues/250) [#116](https://github.com/ngrx/platform/issues/116)
- **Store:** Use injector to get reducers provided via InjectionTokens ([#259](https://github.com/ngrx/platform/issues/259)) ([bd968fa](https://github.com/ngrx/platform/commit/bd968fa)), closes [#189](https://github.com/ngrx/platform/issues/189)

### Features

- **RouterStore:** Add serializer for router state snapshot ([#188](https://github.com/ngrx/platform/issues/188)) ([0fc1bcc](https://github.com/ngrx/platform/commit/0fc1bcc)), closes [#97](https://github.com/ngrx/platform/issues/97) [#104](https://github.com/ngrx/platform/issues/104) [#237](https://github.com/ngrx/platform/issues/237)

<a name="4.0.2"></a>

## [4.0.2](https://github.com/ngrx/platform/compare/v4.0.1...v4.0.2) (2017-08-02)

### Bug Fixes

- **createSelector:** memoize projector function ([#228](https://github.com/ngrx/platform/issues/228)) ([e2f1e57](https://github.com/ngrx/platform/commit/e2f1e57)), closes [#226](https://github.com/ngrx/platform/issues/226)
- **docs:** update angular-cli variable ([eeb7d5d](https://github.com/ngrx/platform/commit/eeb7d5d))
- **Docs:** update effects description ([#164](https://github.com/ngrx/platform/issues/164)) ([c77b2d9](https://github.com/ngrx/platform/commit/c77b2d9))
- **Effects:** Wrap testing source in an Actions observable ([#121](https://github.com/ngrx/platform/issues/121)) ([bfdb83b](https://github.com/ngrx/platform/commit/bfdb83b)), closes [#117](https://github.com/ngrx/platform/issues/117)
- **RouterStore:** Add support for cancellation with CanLoad guard ([#223](https://github.com/ngrx/platform/issues/223)) ([2c006e8](https://github.com/ngrx/platform/commit/2c006e8)), closes [#213](https://github.com/ngrx/platform/issues/213)
- **Store:** Remove auto-memoization of selector functions ([90899f7](https://github.com/ngrx/platform/commit/90899f7)), closes [#118](https://github.com/ngrx/platform/issues/118)

### Features

- **Effects:** Add generic type to the "ofType" operator ([55c13b2](https://github.com/ngrx/platform/commit/55c13b2))
- **Platform:** Introduce [@ngrx](https://github.com/ngrx)/entity ([#207](https://github.com/ngrx/platform/issues/207)) ([9bdfd70](https://github.com/ngrx/platform/commit/9bdfd70))
- **Store:** Add injection token option for feature modules ([#153](https://github.com/ngrx/platform/issues/153)) ([7f77693](https://github.com/ngrx/platform/commit/7f77693)), closes [#116](https://github.com/ngrx/platform/issues/116) [#141](https://github.com/ngrx/platform/issues/141) [#147](https://github.com/ngrx/platform/issues/147)
- **Store:** Added initial state function support for features. Added more tests ([#85](https://github.com/ngrx/platform/issues/85)) ([5e5d7dd](https://github.com/ngrx/platform/commit/5e5d7dd))

<a name="4.0.1"></a>

## [4.0.1](https://github.com/ngrx/platform/compare/v4.0.0...v4.0.1) (2017-07-18)

### Bug Fixes

- **effects:** allow downleveled annotations ([#98](https://github.com/ngrx/platform/issues/98)) ([875b326](https://github.com/ngrx/platform/commit/875b326)), closes [#93](https://github.com/ngrx/platform/issues/93)
- **effects:** make correct export path for testing module ([#96](https://github.com/ngrx/platform/issues/96)) ([a5aad22](https://github.com/ngrx/platform/commit/a5aad22)), closes [#94](https://github.com/ngrx/platform/issues/94)

<a name="4.0.0"></a>

# [4.0.0](https://github.com/ngrx/platform/compare/68bd9df...v4.0.0) (2017-07-18)

### Bug Fixes

- **build:** Fixed deployment of latest master as commit ([#18](https://github.com/ngrx/platform/issues/18)) ([5d0ecf9](https://github.com/ngrx/platform/commit/5d0ecf9))
- **build:** Get tests running for each project ([c4a1054](https://github.com/ngrx/platform/commit/c4a1054))
- **build:** Limit concurrency for lerna bootstrap ([7e7a7d8](https://github.com/ngrx/platform/commit/7e7a7d8))
- **Devtools:** Removed SHOULD_INSTRUMENT token used to eagerly inject providers ([#57](https://github.com/ngrx/platform/issues/57)) ([b90df34](https://github.com/ngrx/platform/commit/b90df34))
- **Effects:** Start child effects after running root effects ([#43](https://github.com/ngrx/platform/issues/43)) ([931adb1](https://github.com/ngrx/platform/commit/931adb1))
- **Effects:** Use Actions generic type for the return of the ofType operator ([d176a11](https://github.com/ngrx/platform/commit/d176a11))
- **Example:** Fix Book State interface parent ([#90](https://github.com/ngrx/platform/issues/90)) ([6982952](https://github.com/ngrx/platform/commit/6982952))
- **example-app:** Suppress StoreDevtoolsConfig compiler warning ([8804156](https://github.com/ngrx/platform/commit/8804156))
- **omit:** Strengthen the type checking of the omit utility function ([3982038](https://github.com/ngrx/platform/commit/3982038))
- **router-store:** NavigationCancel and NavigationError creates a cycle when used with routerReducer ([a085730](https://github.com/ngrx/platform/commit/a085730)), closes [#68](https://github.com/ngrx/platform/issues/68)
- **Store:** Exported initial state tokens ([#65](https://github.com/ngrx/platform/issues/65)) ([4b27b6d](https://github.com/ngrx/platform/commit/4b27b6d))
- **Store:** pass all required arguments to projector ([#74](https://github.com/ngrx/platform/issues/74)) ([9b82b3a](https://github.com/ngrx/platform/commit/9b82b3a))
- **Store:** Remove parameter destructuring for strict mode ([#33](https://github.com/ngrx/platform/issues/33)) ([#77](https://github.com/ngrx/platform/issues/77)) ([c9d6a45](https://github.com/ngrx/platform/commit/c9d6a45))
- **Store:** Removed readonly from type ([#72](https://github.com/ngrx/platform/issues/72)) ([68274c9](https://github.com/ngrx/platform/commit/68274c9))
- **StoreDevtools:** Type InjectionToken for AOT compilation ([e21d688](https://github.com/ngrx/platform/commit/e21d688))

### Code Refactoring

- **Effects:** Simplified AP, added better error reporting and effects stream control ([015107f](https://github.com/ngrx/platform/commit/015107f))

### Features

- **build:** Updated build pipeline for modules ([68bd9df](https://github.com/ngrx/platform/commit/68bd9df))
- **Effects:** Ensure effects are only subscribed to once ([089abdc](https://github.com/ngrx/platform/commit/089abdc))
- **Effects:** Introduce new Effects testing module ([#70](https://github.com/ngrx/platform/issues/70)) ([7dbb571](https://github.com/ngrx/platform/commit/7dbb571))
- **router-store:** Added action types ([#47](https://github.com/ngrx/platform/issues/47)) ([1f67cb3](https://github.com/ngrx/platform/commit/1f67cb3)), closes [#44](https://github.com/ngrx/platform/issues/44)
- **store:** Add 'createSelector' and 'createFeatureSelector' utils ([#10](https://github.com/ngrx/platform/issues/10)) ([41758b1](https://github.com/ngrx/platform/commit/41758b1))
- **Store:** Allow initial state function for AoT compatibility ([#59](https://github.com/ngrx/platform/issues/59)) ([1a166ec](https://github.com/ngrx/platform/commit/1a166ec)), closes [#51](https://github.com/ngrx/platform/issues/51)
- **Store:** Allow parent modules to provide reducers with tokens ([#36](https://github.com/ngrx/platform/issues/36)) ([069b12f](https://github.com/ngrx/platform/commit/069b12f)), closes [#34](https://github.com/ngrx/platform/issues/34)
- **Store:** Simplify API for adding meta-reducers ([#87](https://github.com/ngrx/platform/issues/87)) ([d2295c7](https://github.com/ngrx/platform/commit/d2295c7))

### BREAKING CHANGES

- **Effects:** Effects API for registering effects has been updated to allow for multiple classes to be provided.

BEFORE:

```ts
@NgModule({
  imports: [EffectsModule.run(SourceA), EffectsModule.run(SourceB)],
})
export class AppModule {}
```

AFTER:

```ts
@NgModule({
  imports: [EffectsModule.forRoot([SourceA, SourceB, SourceC])],
})
export class AppModule {}

@NgModule({
  imports: [
    EffectsModule.forFeature([
      FeatureSourceA,
      FeatureSourceB,
      FeatureSourceC,
    ]),
  ],
})
export class SomeFeatureModule {}
```
