---
layout: index

apuntes: T

prev: Desarrollo_basado_en_pruebas
next: Serverless
---

# REST en breve

<!--@
prev: Desarrollo_basado_en_pruebas
next: Serverless
-->

<div class="objetivos" markdown="1">

## Objetivos

### Cubre los siguientes objetivos de la asignatura

1. Conocer los conceptos relacionados con el proceso de virtualización
   tanto de software como de hardware y ponerlos en práctica.
2. Conocer las diferentes tecnologías y herramientas de virtualización
   tanto para procesamiento, comunicación y almacenamiento.

### Objetivos específicos

1. Entender los conceptos necesarios para diseñar, implementar y
   construir una aplicación sobre infraestructura virtual.
2. Diseñar, construir y analizar las prestaciones de una aplicación en
   infraestructura virtual.

</div>

Los
sistemas
[REST (Representational State Transfer)](https://es.wikipedia.org/wiki/Transferencia_de_Estado_Representacional)
usan la sintaxis y semántica
del protocolo HTTP tanto para llevar a cabo peticiones a un
[microservicio](Microservicios) o una función en un
marco [serverless](Serverless).

Las *peticiones* HTTP tienen varias partes diferenciadas:

- Una cabecera HTTP, que contiene metadatos sobre la misma;
  codificación,
  [tipo MIME](https://developer.mozilla.org/es/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types)
  que se está enviando, y, sobre todo, *tokens* que permitan al
  autenticación.
- Un [comando HTTP como PUT o GET](https://developer.mozilla.org/es/docs/Web/HTTP/Methods),
  que indique qué es lo que se quiere que haga.
- Un
  [URI](https://es.wikipedia.org/wiki/Identificador_de_recursos_uniforme),
  o *uniform resource identifier*, un identificador único de un
  recurso sobre cuyo estado se quiere actuar. Para enviar datos en el
  URI, se usa la
  [*codificación porcentaje*](https://en.wikipedia.org/wiki/Percent-encoding)
  que permite meter todo tipo de información con cualquier
  codificación en la parte `query`(la que sigue al `?`, con estructura
  variable = valor).
- Un *cuerpo*, no siempre presente, que contiene los datos que se
  adjuntan a la petición; estos datos pueden ir añadidos como rutas o
  fragmentos en el URI anterior.

Aunque hay 10 comandos HTTP diferentes, en realidad los que más se
usan son sólo
cuatro. Se
[distinguen](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)
por su *idempotencia* (la repetición de un comando sobre un URI dará
el mismo resultado) y *seguros* (cuando no realizan ningún cambio de
estado).

- `GET` es un comando idempotente y seguro, que recupera el contenido
  de un URI.
- `PUT` es idempotente, pero crea o sustituye el estado del URI que se
  use.
- `POST` no es idempotente ni seguro. Se usa para cambiar o parte de
  un recurso, o para crear un recurso cuyo URI no sabemos de antemano.
- `DELETE` es idempotente, pero no seguro.

Lo anterior son convenciones, y lo que se ejecute por omisión
dependerá en realidad de la persona que lo implemente.

La *respuesta HTTP* tendrá una estructura similar, pero incluirá
también
[códigos de estado HTTP](https://developer.mozilla.org/es/docs/Web/HTTP/Status)).
Estos
códigos de estado pueden incluir códigos de error, que tendremos que
interpretar desde nuestra aplicación; los códigos 500 (error del
servidor) no serán códigos que podamos tratar, en general, desde
nuestra aplicación, porque indican que ha habido una excepción no
capturada en la misma.

Es conveniente conocer esta estructura general del protocolo HTTP,
porque se aprovechará para escribir APIs que usen su semántica tanto
para las peticiones como para las respuestas. En estas, diferentes
frameworks ofrecerán un API que permitirá trabajar fácilmente con las
cabeceras, los contenidos y los metadatos correspondientes.

## A dónde ir desde aquí

En el [siguiente tema](Serverless) veremos cómo se usan estas
cabeceras para estructurar peticiones.
