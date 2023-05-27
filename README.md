![HenryLogo](https://d31uz8lwfmyn8g.cloudfront.net/Assets/logo-henry-white-lg.png)

# **VIDEOGAMES** | Proyecto Individual

## **📌 OBJETIVOS**

-  Construir una Single Page Application utlizando las tecnologías: **React**, **Redux**, **Node**, **Express** y **Sequelize**.
-  Poner en práctica recursos básicos de estilos y diseño (UX : UI).
-  Afirmar y conectar los conceptos aprendidos en la carrera.
-  Aprender mejores prácticas.
-  Aprender y practicar el workflow de GIT.
-  Utilizar y practicar testing.

<br />

---

## **⏱ HORARIOS Y FECHAS**

El proyecto individual tiene una duración máxima de tres semanas. Se inicia la primera semana con un Kick-Off, y se agendará una corrección personalizada la última semana.

En el caso de completar todas las tareas antes de dicho lapso se podrá avisar a su instructor para coordinar una fecha de presentación del trabajo (DEMO).

<br />

---

## **⚠️ IMPORTANTE**

Es necesario contar minimamente con la última versión estable de NodeJS y NPM. Asegúrate de contar con ella para poder instalar correctamente las dependecias necesarias para correr el proyecto. Actualmente las versiónes necesarias son:

-  **Node**: 12.18.3 o mayor
-  **NPM**: 6.14.16 o mayor

Para verificar que versión tienes instalada:

```bash
node -v
npm -v
```

**ACLARACIÓN:** las dependencias actuales se encuentran en las versiones que venimos trabajando durante el bootcamp.

-  **react**: ^18.2.0
-  **react-dom**: ^18.2.0
-  **react-router-dom**:^6.11.1
-  **redux**: ^4.2.1
-  **react-redux**: ^8.0.5

Está permitido, **bajo tu responsabilidad**, actualizar las dependencias a versiones más actuales si lo deseas. Versiones mas actuales podrían presentar configuraciones diferentes respecto a las versiones en las que venimos trabajando durante el bootcamp.

### **⛔️ Está rotundamente prohibido utilizar librerías externas para aplicar estilos a la SPA. Tendrás que utilizar CSS mediante algunas de las opciones vistas en el bootcamp (CSS puro, CSS Modules o Styled Components).**

<br />

---

## **📋 SOBRE LA API VIDEOGAMES...**

En este proyecto contarás con una API de Videojuegos que **correrá localmente desde tu computadora**. De esta manera, siempre tendrás disponible esta API externa localmente para poder realizar tu proyecto.

Para que esta API externa quede funcionando desde tu computadora debes, estando en una consola nueva en la carpeta /server, ejecutar el comando 
```npm start```

Podrás ver el mensaje 

``` 
[0] 
[0] > server@1.0.0 server
[0] > nodemon index.js
[0] 
[1] 
[1] > server@1.0.0 api
[1] > echo 'Local API listening on PORT 5000' & json-server --watch api/db.json -p 5000 -q
[1] 
[1] 'Local API listening on PORT 5000' 
[0] [nodemon] 2.0.22
[0] [nodemon] to restart at any time, enter `rs`
[0] [nodemon] watching path(s): *.*
[0] [nodemon] watching extensions: js,mjs,json
[0] [nodemon] starting `node index.js`
[0] Server listening on port 3001

```

Esto significa que la API "externa" ya está corriendo en tu computadora en el puerto 5000 (http://localhost:5000). Debes dejar esta consola abierta para poder comunicarte con la API.

** IMPORTANTE **
No debes modificar **NINGÚN** archivo dentro de la carpeta api. Estos son los archivos que hacen funcionar la API externa. Cualquier modificación en estos archivos puede alterar el funcionamiento normal de la API y de tu proyecto.

<br />

---

## **📋 PARA COMENZAR...**

1. Deberás forkear este repositorio para tener una copia del mismo en tu cuenta personal de GitHub.

2. Clona el repositorio en tu computadora para comenzar a trabajar. Este repositorio contiene un **`BoilerPlate`** con la estructura general del proyecto, tanto del servidor como del cliente. El boilerplate cuenta con dos carpetas: **`server`** y **`client`**. En estas carpetas estará el código del back-end y el front-end respectivamente.

3. En la carpeta **`server`** deberás crear un archivo llamado: **`.env`** que tenga la siguiente forma:

   ```env
       DB_USER=usuariodepostgres
       DB_PASSWORD=passwordDePostgres
       DB_HOST=localhost
   ```

4. Reemplazar **`usuariodepostgres`** y **`passwordDePostgres`** con tus propias credenciales para conectarte a postgres. Este archivo va ser ignorado en la subida a github, ya que contiene información sensible (las credenciales).

5. Adicionalmente será necesario que crees, **desde psql (shell o PGAdmin)**, una base de datos llamada **`videojuegos`**. Si no realizas este paso de manera manual no podrás avanzar con el proyecto.

<br />

---

## **📖 ENUNCIADO GENERAL**

La idea de este proyecto es construir una aplicación web a partir de la API [**videogames**] en la que se pueda:

-  Buscar videojuegos.
-  Visualizar la información de los videojuegos.
-  Filtrarlos.
-  Ordenarlos.
-  Dar de Alta (Crear) nuevo juego.
⚠️ Para las funcionalidades de filtrado y ordenamiento NO se puede utilizar los endpoints de la API externa que ya devuelven los resultados filtrados u ordenados.

**IMPORTANTE**: vas a desarrollar tu PI con un servidor local, para iniciarlo, luego de ejecutar npm i en el backend, vas a tener que ejecutar el siguiente comando: 
npm run api

### Únicos Endpoints/Flags que pueden utilizar

  - GET http://localhost:5000/videogames
  - GET http://localhost:5000/videogames?title_like={title}
  - GET http://localhost:5000/videogames/:{id}


#### Tecnologías necesarias:
- [ ] React
- [ ] Redux
- [ ] Express
- [ ] Sequelize - Postgres

## **📁 INSTRUCCIONES**

<br />

### **🖱 BASE DE DATOS**

Deberás crear dos modelos para tu base de datos. Uno será para los personajes de videojuego y el otro será para los equipos( a los que estén afiliados ). La relación entre ambos modelos debe ser de muchos a muchos. A continuación te dejamos las propiedades que debe tener cada modelo.

**📍 MODELO 1 | Videogames**

-  ID (deben ser distintos a los que vienen de la API). \*
-  Titulo. \*
-  Rating. \*
-  Imagen. \*
-  Equipos \*
-  Descripción. \*

<br />

**📍 MODELO 2 | Genres**

-  ID. \*
-  Nombre. \*

<br />

---

<br />

### **🖱 BACK-END**

Para esta parte deberás construir un servidor utilizando **NodeJS** y **Express**. Tendrás que conectarlo con tu base de datos mediante **Sequelize**.

Tu servidor deberá contar con las siguientes rutas:

#### **📍 GET | /videogames**

-  Obtiene un arreglo de objetos, donde cada objeto es un personaje videojuego con su información.

 IMPORTANTE: Si un videojuego no tiene imagen, deberás colocarle una por defecto 🖼️

#### **📍 GET | /videogames/:id**

-  Esta ruta obtiene el detalle de un personaje específico. Es decir que devuelve un objeto con la información pedida en el detalle de un videojuego.
-  El identificador es recibido por parámetro (ID).
-  Tiene que incluir los datos del/los genero/s a los que este videojuego tiene asociado/s.
-  Debe funcionar tanto para los juegos de la API como para los de la base de datos.

#### **📍 GET | /videogames/title?="..."**

-  Esta ruta debe obtener los primeros 15 personajes que se encuentren con la palabra recibida por query.
-  Debe poder buscarlo independientemente de mayúsculas o minúsculas.
-  Si no existe el videojuego, debe mostrar un mensaje adecuado.
-  Debe buscar tanto los de la API como los de la base de datos.
-  La búsqueda no es exacta, es decir, que debe retornar todos los videojuegos que contengan el texto ingresado

#### **📍 POST | /videogames**

-  Esta ruta recibirá todos los datos necesarios para crear un videojuego y relacionarlo con sus generos solicitados.
-  Toda la información debe ser recibida por body.
-  Debe crear un nuevo videojuego en la base de datos, y este debe estar relacionado con sus generos (dos o más ).

#### **📍 GET | /videogames**

-  Obtiene un arreglo con todos los generos existentes de la API.
-  En una primera instancia, cuando la base de datos este vacía, deberás guardar todos los géneros que encuentres en la API.
-  Estos deben ser obtenidos de la consulta al enpoint de la API(se evaluará que no haya hardcodeo). Luego de obtenerlos, deben ser guardados en la base de datos para su posterior consumo desde allí.

<br />

---

<br />

### **🖱 FRONT-END**

Se debe desarrollar una aplicación utilizando **React** y **Redux** que contenga las siguientes vistas:

**📍 LANDING PAGE |** deberás crear una página de inicio o bienvenida con:

-  Alguna imagen de fondo representativa al proyecto.
-  Botón para ingresar a la **`home page`**.

<br />

**📍 HOME PAGE |** la página principal de tu SPA debe contener:

-  SearchBar: un input de búsqueda para encontrar videojuegos por nombre.
-  Sector en el que se vea un listado de cards con los videojuegos. Al iniciar deberá cargar los primeros resultados obtenidos desde la ruta **`GET /videogames`** y deberá mostrar su:
   -  Imagen.
   -  Título.
   -  Géneros Asociados.
-  Cuando se le hace click a una Card deberá redirigir al detalle de ese videojuego específico.
-  Botones/Opciones para **filtrar** por genero, y por si su origen es de la API o de la base de datos (creados por nosotros desde el formulario).
-  Botones/Opciones para **ordenar** tanto ascendentemente como descendentemente a los juegos por orden alfabético y por rating.
-  Paginado: el listado de tus juegos se hará por partes. Tu SPA debe contar con un paginado que muestre un total de 15 videojuegos por página.

**⚠️ IMPORTANTE**: se deben mostrar tanto los videojuegos traidos desde la API como así también los de la base de datos, pero **NO** está permitido almacenar en la base de datos los juegos de la API. **Solamente se pueden guardar aquellos creados desde el form**.


<br />

**📍 DETAIL PAGE |** en esta vista se deberá mostrar toda la información específica de un videojuego:

-  ID.
-  Titulo.
-  Rating.
-  Imagen. 
-  Descripción. 
-  Equipos
-  Géneros Asociados


**📍 FORM PAGE |**: en esta vista se encontrará el formulario para crear un nuevo videojuego.

Este formulario debe ser **controlado completamente con JavaScritp**. No se pueden utilizar validaciones HTML, ni utilizar librerías especiales para esto. Debe contar con los siguientes campos:


-  Titulo.
-  Rating.
-  Imagen. 
-  Descripción. 
-  Equipos
-  Posibilidad de seleccionar/agregar varios géneros en simultáneo.
-  Botón para dar de alta (crear) el nuevo videojuego.

> [**IMPORTANTE**]: es requisito que el formulario de creación esté validado sólo con JavaScript. Puedes agregar las validaciones que consideres. Por ejemplo: que el nombre del videojuego no pueda contener símbolos,etc.

<br />

---

<br />

### **🖱 TESTING**

Ten en cuenta que en esta instancia no es obligatorio el desarrollo de testing para tu aplicación. De igual manera, te desafiamos a que los hagas, ¡ya que suman puntos!

-  Al menos tener un componente del frontend con sus tests respectivos.
-  Al menos tener dos ruta del backend con sus tests respectivos.
-  Al menos tener un modelo de la base de datos con sus tests respectivos.



<br />


<br />

---

<br />

<div align="center">
<img src="./videogame.png" alt="" />
</div>
