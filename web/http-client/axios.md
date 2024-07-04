# Axios

Axios es un Cliente HTTP basado en promesas para node.js y el navegador. Es isomorfico (puede ejecutarse en el navegador y NodeJS con el mismo código base). En el lado del servidor usa el modulo nativo http de node.js, mientras que en el lado del cliente (navegador) usa XMLHttpRequests.

Al ser HTTP usa los **verbos HTML**

## Instalar la dependencia

```bash
npm i axios
```

## Usar axios

Como es un cliente HTTP seguramente lo usara como un modulo, por lo que es necesario exportar las funciones que implemente

```js
import axios from "axios";

// Json Server DB
const baseUrl = "http://localhost:3000/notes";

const getAll = () => {
  const request = axios.get(baseUrl);
  // Axios se basa en promesas, por eso se trata con then catch
  return request.then((response) => response.data);
};

const update = (id, newObject) => {
  const request = axios.put(`$(baseUrl)/$(id)`, newObject);
  return request.then((response) => response.data);
};

export default { getAll, update };
```

```js
// Common JS
const axios = require("axios");

// Hacer una petición para un usuario con ID especifico
axios
  .get("/user?ID=12345")
  .then(function (response) {
    // manejar respuesta exitosa
    console.log(response);
  })
  .catch(function (error) {
    // manejar error
    console.log(error);
  })
  .finally(function () {
    // siempre sera executado
  });

// Opcionalmente, la solicitud anterior también se puede realizar como
axios
  .get("/user", {
    params: {
      ID: 12345,
    },
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  })
  .finally(function () {
    // siempre sera ejecutado
  });

// ¿Quieres usar async/await? Añade la palabra reservada `async` a tu función/método externo.
async function getUser() {
  try {
    const response = await axios.get("/user?ID=12345");
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
```
