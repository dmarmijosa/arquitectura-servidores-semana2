# Posts API

API HTTP construida con Node.js, Express y TypeScript para gestionar posts.

## Índice

- [Descripción](#descripción)
- [Requisitos previos](#requisitos-previos)
- [Instalación](#instalación)
- [Ejecución del servidor](#ejecución-del-servidor)
- [Ejecución de pruebas](#ejecución-de-pruebas)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Endpoints de la API](#endpoints-de-la-api)
- [Colección de Postman](#colección-de-postman)
- [Autor](#autor)

## Descripción

Esta API permite realizar operaciones CRUD (crear, leer, actualizar y eliminar) sobre una colección de posts almacenados en una base de datos MongoDB. Está desarrollada utilizando las siguientes tecnologías:

- **Node.js**
- **Express**
- **TypeScript**
- **Mongoose**

## Requisitos previos

- **Node.js** v14 o superior
- **npm** v6 o superior
- **MongoDB** corriendo en `localhost`

## Instalación

1. **Clona este repositorio**:

   ```bash
   git clone https://github.com/dmarmijosa/arquitectura-servidores-semana2
   cd semana2
   ```

2. **Instala las dependencias**:

   ```bash
   npm install
   ```

## Ejecución del servidor

### Modo de desarrollo

Para ejecutar el servidor en modo de desarrollo con recarga automática:

```bash
npm run dev
```

El servidor estará escuchando en `http://localhost:8000`.

### Modo de producción

Para compilar y ejecutar el servidor en modo de producción:

```bash
npm run build
npm start
```

## Ejecución de pruebas

Para ejecutar las pruebas unitarias con Jest y Supertest:

```bash
npm run test
```

## Estructura del proyecto

El proyecto sigue una estructura modular para facilitar la escalabilidad y el mantenimiento:

```
posts-api/
├── /
│   ├── app.ts                  // Archivo principal de la aplicación
│   ├── bin/
│   │   └── www.ts              // Archivo de arranque del servidor
│   ├── config/
│   │   └── db.config.ts        // Configuración de la base de datos
│   ├── controllers/
│   │   └── post.controller.ts  // Controladores de posts
│   ├── models/
│   │   └── post.model.ts        // Modelo de datos de Post
│   ├── routes/
│   │   └── post.route.ts      // Rutas de posts
│   ├── tests/
│   └── posts.spec.test.ts           // Pruebas unitarias
├── dist/                       // Archivos compilados
├── package.json
├── tsconfig.json
├── jest.config.js
├── README.md
```

## Endpoints de la API

### 1. Crear un nuevo Post

- **Método**: `POST`
- **URL**: `/api/posts`
- **Descripción**: Crea un nuevo post en la base de datos.
- **Body**: Debe incluir `title`, `text` y `author`.
- **Ejemplo de JSON**:

  ```json
  {
    "title": "Sample Post for Testing",
    "text": "This is a sample post used to test the functionality of the API. It contains sufficient text to ensure that all validation rules are met.",
    "author": "Test Author"
  }
  ```

- **Respuestas**:
  - **201 Created**: Devuelve el post creado.
  - **400 Bad Request**: Si hay errores en los datos proporcionados.

### 2. Obtener todos los Posts

- **Método**: `GET`
- **URL**: `/api/posts`
- **Descripción**: Devuelve todos los posts almacenados en la base de datos.
- **Respuestas**:
  - **200 OK**: Devuelve una lista de posts.

### 3. Obtener un Post por ID

- **Método**: `GET`
- **URL**: `/api/posts/:id`
- **Descripción**: Devuelve el post cuyo ID coincide con el proporcionado.
- **Respuestas**:
  - **200 OK**: Devuelve el post solicitado.
  - **404 Not Found**: Si el post no existe.

### 4. Actualizar un Post por ID

- **Método**: `PATCH`
- **URL**: `/api/posts/:id`
- **Descripción**: Actualiza los campos del post cuyo ID coincide con el proporcionado.
- **Body**: Puede incluir `title`, `text` o `author`.
- **Respuestas**:
  - **200 OK**: Devuelve el post actualizado.
  - **404 Not Found**: Si el post no existe.

### 5. Eliminar un Post por ID

- **Método**: `DELETE`
- **URL**: `/api/posts/:id`
- **Descripción**: Elimina el post cuyo ID coincide con el proporcionado.
- **Respuestas**:
  - **204 No Content**: Si el post fue eliminado.
  - **404 Not Found**: Si el post no existe.

## Colección de Postman

La colección de Postman se encuentra en la carpeta `postman/PSEMANA 2 ARQUITECTURA SERVIDORES.postman_collection`. Contiene peticiones preconfiguradas para todos los endpoints mencionados.

**Cómo importar la colección en Postman**:

1. Abre Postman.
2. Haz clic en **Import**.
3. Selecciona el archivo `SEMANA 2 ARQUITECTURA SERVIDORES.postman_collection` desde la carpeta `postman`.
4. La colección aparecerá en tu lista de colecciones.

## Autor

- **Danny Armijos** - [Danny Armijos](https://github.com/dmarmijosa)

