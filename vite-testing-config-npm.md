# Instalación y configuracion de Jest + React Testing Library

## En proyectos de React + Vite

1. Instalaciones:

```
npm install --save-dev jest
npm install --save-dev babel-jest @babel/core @babel/preset-env @babel/preset-react react-test-renderer
npm install --save-dev @testing-library/react @types/jest jest-environment-jsdom
```

2. Opcional: Si usamos Fetch API en el proyecto:

```
npm i --save-dev whatwg-fetch
```

3. Actualizar los scripts del **package.json**

```
"scripts: {
  ...
  "test": "jest --watchAll"
```

4. Crear la configuración de babel **babel.config.cjs**

```
module.exports = {
    presets: [
        [ '@babel/preset-env', { targets: { esmodules: true } } ],
        [ '@babel/preset-react', { runtime: 'automatic' } ],
    ],
};
```

5. Opcional, pero eventualmente necesario, crear Jest config y setup:

**jest.config.cjs**

```
/** @type {import('jest').Config} */
const config = {
	verbose: true,
	setupFiles: ['./jest.setup.js'],
	testEnvironment: 'jest-environment-jsdom',
};

module.exports = config;
```

**jest.setup.js**

```
// En caso de necesitar la implementación del FetchAPI
import 'whatwg-fetch';
```

6. Opcional, para instalar los propTypes**

```
npm i prop-types
```
