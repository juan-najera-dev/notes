# JSON SERVER

API REST para desarrollo, permite el manejo de json como db

```bash
# Normal
npm i json-server

# Compartir con Desarrollo
npm i json-server --share-dev
```

## Estructura de la base de datos json db.json

```json
{
  "nombreDB1": [
    {
      "Registro1llave1": "valor1",
      "Registro1llave2": "valor2",
      "Registro1llave3": "valor3"
    },
    {
      "Registro2llave1": "valor1",
      "Registro2llave2": "valor2",
      "Registro2llave3": "valor3"
    }
  ],

  "nombreDB2": ["..."]
}
```

## Agregar como Script a package.json

Para agregarlo como script en el **packaage.json** en la parte de **scripts** se pone

```json
"scripts" {
	"server": "json-server --watch db.json --port 3000"
}
```

## Ejecutar el servidor con Node

Para ejecutarlo

```bash
npx json-server --watch db.json --port 3000
```
