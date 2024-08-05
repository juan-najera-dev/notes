# Tailwind

1. Crear una nueva carpeta

```bash
mkdir nombreDelProyecto
cd nombreDelProyecto
```

2. Dentro de la carpeta crear el archivo package.json con el comando

```bash
npm init -y
```

3. Descargar tailwind y añadir al package.json la dependencia de tailwind

```bash
npm install -D tailwindcss
```

4. Crear el archivo tailwind.config.js

```bash
npx tailwindcss init
```

5. Crear la carpeta src

```bash
mkdir src
```

6. Crear el index.html

```bash
cd src
touch index.html
```

7. Copiar el contenido del index.html

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link href="./css/output.css" rel="stylesheet" />
  </head>
  <body>
    <h1 class="text-3xl font-bold underline">Hello world!</h1>
  </body>
</html>
```

8. Crear la carpeta css y los archivos input.css y output.css

```bash
mkdir css
touch css/input.css
touch css/output.css
```

9. Agregar al archivo input.css las siguientes lineas

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

10. Agregar los directorios donde se van a buscar los archivos html y js en el archivo tailwind.config.js

> [!NOTE]
> Solo se modifica la linea de content

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

1.  En el archivo package.json en la seccion de scripts agregar el comando de ejecucion de tailwind

> [!NOTE]
> Solo se agrega la linea "dev", pero se puede nombrar de cualquier manera

```json
"scripts": {
    "dev": "npx tailwindcss -i ./src/css/input.css -o ./src/css/output.css --watch"
  }
```

12. Se puede ejecutar desde la terminal o usando la ejecucion del script con el nombre asignado

```bash
npx tailwindcss -i ./src/input.css -o ./src/output.css --watch
npm run nombreDelScriptComoQuedoEnElPackageJson
```
