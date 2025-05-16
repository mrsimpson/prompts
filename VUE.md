# Tech stack

- Typescript
- Limit language scope to node-js compatibility (--strip-types compatible)
- vite as build tool
- express for servers
- vitest for testing
- Vue3 with composition API (script setup)

# Project structure

```
/src
|-- /components
|   |-- BaseButton.vue
|   |-- BaseCard.vue
|   |-- PokemonList.vue
|   |-- PokemonCard.vue
|-- /composables
|   |-- usePokemon.ts
|-- /utils
|   |-- validators.ts
|-- /layout
|   |-- DefaultLayout.vue
|   |-- AdminLayout.vue
|-- /plugins
|   |-- translate.ts
|-- /views
|   |-- Home.vue
|   |-- PokemonDetail.vue
|-- /router
|   |-- index.ts
|-- /store
|   |-- index.ts
|-- /assets
|   |-- /images
|   |-- /styles
|-- /tests
|   |-- ...
|-- App.vue
|-- main.ts

```

# Conventions

## Naming Conventions

- **Variables and Functions**: Use camelCase
  ```typescript
  const userData = getUserInformation()
  function calculateTotalPrice(items) { /* ... */ }
  ```

- **Classes**: Use PascalCase
  ```typescript
  class UserAccount {
    // ...
  }
  ```

- **Interfaces**: Use PascalCase with descriptive names
  ```typescript
  interface UserProfile {
    id: string
    name: string
    email: string
  }
  ```

- **Constants**: Use UPPER_SNAKE_CASE for true constants
  ```typescript
  const MAX_RETRY_ATTEMPTS = 3
  ```

- **File names**: Use kebab-case for files
  ```
  user-service.ts
  auth-middleware.ts
  ```

## File organization

- Single responsibility principle: Only one exported member per file
- sub-folders define logical packages. An index.ts exposes the packages public components