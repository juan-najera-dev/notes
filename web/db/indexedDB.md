# Indexed DB

Base de datos incorporada en todos los navegadores, permite almacenar informacion de forma local a diferencia de localStorage que permite almacenar 10mb esta no tiene restricciones

> [!NOTE]
> La informacion **se almacena del lado del cliente**, no debe usarse para guardar informacion sensible

## Conexion a la base de datos

```js
// Variable de referencia a la conexion de ls DB
let db;

function pruebaDB() {
  // crear base de datos con la versión 1
  let pruebaDB = window.indexedDB.open("dbPrueba", 1.1);

  // si hay un error, lanzarlo
  pruebaDB.onerror = function () {
    console.log("pruebaDB: Hubo un error");
  };
  // si todo esta bien, asignar a database el resultado
  pruebaDB.onsuccess = function () {
    console.log("pruebaDB: todo listo!");
    // guarda el resultado
    db = pruebaDB.result;
    console.log("pruebaDB\n", DB);
  };

  // este método solo corre una vez, se usa para definir el modelo de la base de datos (la estructura) en caso de que no exista

  pruebaDB.onupgradeneeded = function (e) {
    // el evento que se va a correr toma la base de datos
    let db = e.target.result;

    // definir el objectstore, primer parametro el nombre de la DB, segundo las opciones
    // keypath es de donde se van a obtener los indices (llave primaria)
    let objectStore = db.createObjectStore("dbPrueba", {
      keyPath: "id",
      // Gestion de la primary key
      autoIncrement: true,
    });

    //createindex, nombre y keypath, 3ro los parametros, keypath en este caso sera el indice para poder realizar busquedas
    objectStore.createIndex("nombre", "nombre", { unique: false });
    objectStore.createIndex("email", "email", { unique: true });
    objectStore.createIndex("telefono", "telefono", { unique: false });
    objectStore.createIndex("id", "id", { unique: true });
    console.log("pruebaDB: creada y lista");
  };
}

function crearCliente() {
  // Crear un nuevo registro
  let transaction = db.transaction(["prueba"], "readwrite");
  transaction.oncomplete = function (event) {
    console.log("crearCliente: Transacción Completada");
  };
  transaction.onerror = function (event) {
    console.log("creaCliente: Hubo un error en la transacción");
  };
  let objectStore = transaction.objectStore("prueba");
  console.log("creaCliente:", objectStore);
  const nuevoCliente = {
    nombre: "Pedro",
    email: "correo@correo.com",
    telefono: 102092212,
    id: "2acd",
  };
  let peticion = objectStore.add(nuevoCliente);
  console.log("crearCliente peticion:", peticion);
}

function obtenerClientes() {
  let abrirConexion = window.indexedDB.open("dbPrueba", 1.1);
  // si hay un error, lanzarlo
  abrirConexion.onerror = function () {
    console.log("Hubo un error");
  };
  // si todo esta bien, asignar a database el resultado
  abrirConexion.onsuccess = function () {
    // guardamos el resultado
    db = abrirConexion.result;
    const objectStore = db.transaction("dbPrueba").objectStore("prueba");

    // retorna un objeto request o petición,
    objectStore.openCursor().onsuccess = function (e) {
      // cursor se va a ubicar en el registro indicado para accede ra los datos
      const cursor = e.target.result;

      //  console.log(e.target);

      // Note que el cursor es la bandera que indica si hay datos, no es necesario ponerla en un ciclo o evaluar si tiene un siguiente

      if (cursor) {
        const { nombre, empresa, email, telefono, id } = cursor.value;
        console.log("nombre", nombre);
        console.log("empresa", empresa);
        console.log("email", email);
        console.log("telefono", telefono);
        console.log("id", id);
        cursor.continue();
      } else {
        console.log("No hay registros o mas registris");
      }
    };
  };
}
```
