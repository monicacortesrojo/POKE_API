Creamos un json y su backup que es la que vamos a alterar y corromper.

No vamos a usar un módulo de node porque es menos flexible y con el json vamos a poder alterarlo a tiempo real. Nos acercamos a la realidad de una base de datos de mongo.

Creamos nuestra api.js
npm init
requerimos express: npm install express
hacemos nuestro primer endpoint GET

# MÉTODO POST

Era para enviar información a la api

## POR QUERY PARAMS

La primera forma es por parámetros. ESTA MODIFICA NUESTRA URL
Hacemos una querystring que es mostrar los parametros en la url.
http://localhost:1010/api/pokemons?name=pikachu&type=electrico

Tenemos primero la url y despues de la ? viene la query string y aqui vemos parametro = valor & parametro = valor

enviamos el post desde postman y debugeamos, vamos a request y aqui detro de query vamos a ver lo que se ha enviado y desde ahi acceder al propio objeto.

## POR BODY

La URL no se nos modifica por lo tanto mantenemos la info más privada
x-www-form-
para esto tenemos que configurar lo siguiente
const bodyParser = require("body-parser");
api.use(bodyParser.urlencoded({extended:true}));
para esta tenemos que entrar dentro de request.body.lo que sea

## POR PARAMS ÚNICAMENTE

A esto se accede con request.params, sin el query
api.get("/api/pokemons/:id")

## PAGINADO

?limit=10&offset=0

Esto es en la request, es un filtrado de tu base de datos

### Limit

El numero de elementos que me trae la llamada

### Offset

El numero donde empieza la llamada
Es el limite + 1

## Forma más sencilla

Solo indicar el número de página que quieres

http://localhost:1010/api/pokemons/page/1
api/pokemons/page/{page}

## SUBRECURSOS

Si tenemos dentro de nuestra array de objetos un objeto con otra array con subobjetos accedemos asi

/api/pokemons/:id/location/:locationId ESTE SERIA EL ENDPOINT
