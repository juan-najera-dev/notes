# Colors

Agregar colores a la terminal para mejorar la lectura del console.log

## Instalacion de dependencia de desarrollo

```bash
npm i -D colors
```

## Uso

```js
import colors from "colors";

// Imprime con letra roja
console.log(colors.red("Esto es un error"));
// Imprime en fondo rojo letra blanca
console.log(colors.bgRed.white("Esto es un error"));
// Imprime en fondo negro letra roja
console.log(colors.bgBlack.red("Esto es un error"));
```
