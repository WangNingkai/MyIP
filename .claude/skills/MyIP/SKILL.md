```markdown
# MyIP Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches the core development patterns and workflows used in the MyIP repository, a JavaScript project built with Vite and Vue. It covers conventions for file naming, imports/exports, commit styles, and provides step-by-step guides for common workflows such as adding API endpoints, developing features with localization and tests, improving UI/localization, and updating cache/build configurations. Example code snippets and command suggestions are included to streamline contributions and ensure consistency.

## Coding Conventions

- **File Naming:**  
  Use camelCase for JavaScript files.  
  _Example:_  
  ```
  backendServer.js
  registerServiceWorker.js
  ```

- **Import Style:**  
  Use relative imports for modules.  
  _Example:_  
  ```js
  import { fetchData } from './utils/apiHelper.js';
  import MyComponent from '../components/MyComponent.vue';
  ```

- **Export Style:**  
  Use named exports.  
  _Example:_  
  ```js
  // In utils/apiHelper.js
  export function fetchData(url) { ... }
  export const API_URL = 'https://api.example.com';
  ```

- **Commit Message Patterns:**  
  - Types: `feat`, `fix`, `refactor`
  - Prefix usage:  
    ```
    feat: add user authentication
    fix: correct IP address parsing bug
    refactor: improve API handler structure
    ```
  - Average commit message length: ~37 characters

## Workflows

### Add or Enhance API Endpoint
**Trigger:** When you want to add a new API endpoint or significantly enhance backend API functionality.  
**Command:** `/new-api-endpoint`

1. Create or update the relevant handler in `api/handler.js` (or another file in `api/`).
2. Register the new route or middleware in `backend-server.js`.
3. Update or create documentation in `api/AGENTS.md` and/or `AGENTS.md`.
4. If new environment variables are needed, update `.env.example`.
5. Update frontend components to consume the new endpoint as needed.
6. Update `frontend/data/changelog.json` and bump the version in `package.json`.

_Example:_
```js
// api/ipLookup.js
export function ipLookupHandler(req, res) {
  // Handler logic
}
```
```js
// backend-server.js
import { ipLookupHandler } from './api/ipLookup.js';
app.get('/api/ip-lookup', ipLookupHandler);
```

### Feature Development with i18n and Tests
**Trigger:** When adding or improving a feature that affects the UI and needs localization and tests.  
**Command:** `/feature-i18n-test`

1. Edit or create `frontend/components/*.vue` files for the feature.
2. Update localization files:  
   - `frontend/locales/en.json`
   - `frontend/locales/fr.json`
   - `frontend/locales/tr.json`
   - `frontend/locales/zh.json`
3. Add or update relevant test files in `tests/*.js`.
4. Update `frontend/data/changelog.json` if the feature is user-facing.
5. Bump the version in `package.json` if needed.

_Example:_
```vue
<!-- frontend/components/IpDisplay.vue -->
<template>
  <div>{{ $t('your_ip') }}: {{ ip }}</div>
</template>
<script>
export default {
  props: ['ip']
}
</script>
```
```json
// frontend/locales/en.json
{
  "your_ip": "Your IP"
}
```
```js
// tests/ipDisplay.test.js
import { mount } from '@vue/test-utils';
import IpDisplay from '../frontend/components/IpDisplay.vue';

test('displays IP', () => {
  const wrapper = mount(IpDisplay, { props: { ip: '127.0.0.1' } });
  expect(wrapper.text()).toContain('127.0.0.1');
});
```

### UI or Localization Improvement
**Trigger:** When making minor UI tweaks or updating translations for clarity or completeness.  
**Command:** `/ui-i18n-improve`

1. Edit the relevant Vue component(s) in `frontend/components/`.
2. Update one or more localization files in `frontend/locales/`.
3. Optionally, update `frontend/data/changelog.json`.

_Example:_
```vue
<!-- frontend/components/LanguageSelector.vue -->
<template>
  <select v-model="locale">
    <option value="en">{{ $t('english') }}</option>
    <option value="fr">{{ $t('french') }}</option>
    <!-- ... -->
  </select>
</template>
```
```json
// frontend/locales/en.json
{
  "english": "English",
  "french": "French"
}
```

### Cache or Build Configuration Update
**Trigger:** When optimizing caching, removing outdated service worker code, or adjusting build settings.  
**Command:** `/update-cache-config`

1. Edit `frontend-server.js` or `backend-server.js` to adjust cache headers.
2. Modify or remove `frontend/utils/register-service-worker.js` or `unregister-service-worker.js`.
3. Update `frontend/sw.js` if service worker logic changes.
4. Edit `vite.config.js` or `package.json` for build adjustments.
5. Update documentation in `AGENTS.md` if needed.

_Example:_
```js
// frontend-server.js
app.use((req, res, next) => {
  res.setHeader('Cache-Control', 'public, max-age=3600');
  next();
});
```
```js
// vite.config.js
export default {
  build: {
    sourcemap: true
  }
};
```

## Testing Patterns

- **Test File Pattern:**  
  Test files are named `*.test.js` and typically reside in a `tests/` directory.
- **Framework:**  
  The specific test framework is not specified, but examples suggest usage of a modern JS test runner (e.g., Jest or Vitest).
- **Example Test:**
  ```js
  // tests/apiHandler.test.js
  import { apiHandler } from '../api/handler.js';

  test('returns correct response', () => {
    const req = { ... };
    const res = { ... };
    apiHandler(req, res);
    expect(res.status).toBe(200);
  });
  ```

## Commands

| Command              | Purpose                                                         |
|----------------------|-----------------------------------------------------------------|
| /new-api-endpoint    | Add or enhance an API endpoint and update related documentation |
| /feature-i18n-test   | Develop or refactor a feature with localization and tests       |
| /ui-i18n-improve     | Make minor UI or localization improvements                     |
| /update-cache-config | Update cache strategies or build configuration                  |
```
