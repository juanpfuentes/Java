# API Rest  #

## Introducción ##

Una API (Application Programming Interface) es un conjunto de reglas y protocolos que permite que diferentes sistemas interactúen y compartan información y servicios. Una API define cómo debe realizarse una petición y qué respuesta se espera recibir, permitiendo que diferentes aplicaciones interactúen sin necesidad de comprender el código subyacente de la otra aplicación.

Las API pueden ser de diferentes tipos, como por ejemplo:

API de sistema operativo: permite que los programas accedan a los servicios del sistema operativo.
API de biblioteca: permite que los programas accedan a las funciones de una biblioteca específica.
API de red: permite que los programas interactúen con un servidor remoto a través de una red.
En el contexto de la web, una API REST (Representational State Transfer) es un tipo de API que utiliza HTTP para permitir que los programas interactúen con un servidor remoto a través de la web. La API REST utiliza los verbos HTTP (GET, POST, PUT, DELETE, etc.) para realizar peticiones y obtener respuestas en formato JSON o XML.

Una API REST se basa en el concepto de recursos, donde cada recurso es identificado por una URL única. La respuesta a una petición a una URL determinada puede ser en formato JSON o XML, dependiendo de la configuración de la API. Las APIs REST son ampliamente utilizadas en aplicaciones web y móviles para acceder a datos y funcionalidades de servidores remotos.

## Verbos ##

Los verbos HTTP más comunes utilizados en una API REST incluyen:

GET: Obtiene un recurso o una lista de recursos
Ejemplo:

```
GET /users/1
```

POST: Crea un nuevo recurso
Ejemplo:

```
POST /users
{
  "username": "johndoe",
  "email": "johndoe@example.com"
}
```

PUT: Actualiza un recurso existente
Ejemplo:

```
PUT /users/1
{
  "username": "janedoe",
  "email": "janedoe@example.com"
}
```

DELETE: Elimina un recurso existente
Ejemplo:

```
DELETE /users/1
```

Estos verbos HTTP se utilizan para representar las operaciones CRUD (Crear, Leer, Actualizar y Borrar) en una API REST. Además de estos verbos, también existen otros verbos HTTP como PATCH, OPTIONS, etc. que se utilizan menos comúnmente.

## Postman ##

Postman es una herramienta para desarrolladores que les permite probar APIs. Con Postman, puedes enviar peticiones HTTP y ver las respuestas de manera fácil y visual. Además, ofrece características como guardar y compartir colecciones de peticiones, automatización de pruebas, monitoreo de API y mucho más.

Para instalar Postman, siga estos pasos:

Visite el sitio web de Postman en https://www.postman.com/
Haga clic en el botón "Download" para descargar la versión adecuada para su sistema operativo.
Ejecute el archivo de instalación y siga las instrucciones en pantalla.
Una vez instalado, abra la aplicación y cree una cuenta si desea usar todas las funciones de la versión gratuita.
Ahora estás listo para usar Postman. Puedes crear una nueva solicitud haciendo clic en el botón "New" y seleccionando "Request". Luego, especifique la URL de la API que desea probar, seleccione el verbo HTTP deseado (GET, POST, PUT, DELETE, etc.) y agregue cualquier parámetro o cabecera necesarios antes de enviar la solicitud.

## APis para usar ##

https://randomuser.me/

Tan sencillo como esto:

```
$.ajax({
  url: 'https://randomuser.me/api/',
  dataType: 'json',
  success: function(data) {
    console.log(data);
  }
});
```
https://deckofcardsapi.com/

https://rickandmortyapi.com/documentation/#rest

http://avatars.adorable.io/#demo

https://www.sitepoint.com/rest-api/

