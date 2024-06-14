# Proyecto de Configuración de Pruebas con Vitest y Testing Library

Configuración basica para utilizar Vitest junto con Testing Library para realizar pruebas en una aplicación React.

## Instalación

Primero, instala las dependencias necesarias:

```sh
npm i -D vitest jsdom @testing-library/jest-dom @testing-library/react
```

## Configuración

### Archivo de configuración para las pruebas

Crea un archivo de configuración para las pruebas en `src/__tests__/setup.js` con el siguiente contenido:

```js
import '@testing-library/jest-dom';
```

### Actualización de `vite.config.js`

Actualiza el archivo `vite.config.js` para incluir la configuración de Vitest:

```js
import { defineConfig } from "vitest/config";
import react from '@vitejs/plugin-react-swc';

export default defineConfig({
    plugins: [react()],
    test: {
        globals: true,
        environment: 'jsdom',
        setupFiles: ['src/__tests__/setup.js'],
        include: ['src/**/*.{test,spec}.{js,ts,jsx,tsx}']
    },
});
```

### Script de pruebas en `package.json`

Añade el siguiente script de pruebas a tu `package.json`:

```json
"scripts": {
    "test": "vitest"
}
```

## Uso

Para ejecutar las pruebas, utiliza el siguiente comando:

```sh
npm run test
```

Esto iniciará Vitest y ejecutará todas las pruebas en tu proyecto que coincidan con el patrón de archivos especificado en la configuración.

---

