# Task Management REST API

API REST para la gestión de tareas, desarrollada con **Node.js, Express y MongoDB**. Incluye registro e inicio de sesión de usuarios, autenticación mediante JSON Web Tokens (JWT) y operaciones CRUD sobre tareas.

## Tecnologías

- Node.js y Express
- MongoDB y Mongoose
- JSON Web Tokens (JWT)
- bcrypt para el hash de contraseñas
- express-validator para validar datos
- dotenv para gestionar variables de entorno

## Funcionalidades

- Registro de usuarios con validación de correo electrónico y contraseña.
- Inicio de sesión mediante correo electrónico y contraseña.
- Generación de tokens JWT con expiración de una hora.
- Protección de rutas mediante middleware de autenticación.
- Creación, consulta, actualización y eliminación de tareas.
- Almacenamiento de usuarios y tareas en MongoDB.
- Manejo de errores HTTP.

## Instalación

**1. Clonar el repositorio**

```bash
git clone https://github.com/karolu5/CRUD-node-mongo.git
cd CRUD-node-mongo
```

**2. Instalar dependencias**

```bash
npm install
```

**3. Configurar variables de entorno**

Crear un archivo `.env` en la raíz del proyecto:

```dotenv
MONGO_URI=mongodb://localhost:27017/tareasBD
JWT_SECRET=tu_clave_aleatoria_segura
PORT=3000
```

Reemplazar `JWT_SECRET` por una clave aleatoria segura. No compartir ni subir el archivo `.env` al repositorio.

**4. Iniciar MongoDB**

Asegurarse de que el servidor MongoDB esté ejecutándose y sea accesible mediante `MONGO_URI`.

**5. Iniciar la aplicación**

```bash
npm start
```

El servidor utiliza el puerto 3000 de forma predeterminada.

## Endpoints de autenticación

### Registrar usuario

`POST /auth/register`

```json
{
  "email": "usuario@ejemplo.com",
  "password": "contraseña123"
}
```

La contraseña debe contener al menos seis caracteres.

### Iniciar sesión

`POST /auth/login`

```json
{
  "email": "usuario@ejemplo.com",
  "password": "contraseña123"
}
```

La respuesta incluye un token JWT que se utiliza para acceder a las rutas protegidas.

## Endpoints de tareas

Todas las rutas de tareas requieren autenticación mediante el encabezado:

```http
Authorization: Bearer TU_TOKEN
```

| Método | Ruta | Descripción |
|---|---|---|
| GET | `/tareas` | Obtener todas las tareas |
| GET | `/tareas/:id` | Obtener una tarea por ID |
| POST | `/tareas` | Crear una tarea |
| PUT | `/tareas/:id` | Actualizar una tarea |
| DELETE | `/tareas/:id` | Eliminar una tarea |

### Ejemplo: crear una tarea

`POST /tareas`

```json
{
  "texto": "Aprender MongoDB"
}
```

### Ejemplo: actualizar una tarea

`PUT /tareas/:id`

```json
{
  "texto": "Practicar consultas con MongoDB"
}
```

## Estructura del proyecto

```text
CRUD-node-mongo/
├── index.js
├── middleware/
│   ├── authMiddleware.js
│   └── errorHandler.js
├── models/
│   ├── tarea.model.js
│   └── usuario.model.js
├── routes/
│   ├── auth.routes.js
│   └── tarea.routes.js
├── package.json
├── package-lock.json
└── README.md
```

## Consideraciones

Este proyecto es una implementación de práctica de una API REST con autenticación y persistencia de datos.

Actualmente, las tareas se consultan de manera global: no están asociadas a un usuario específico. Una mejora futura sería relacionar cada tarea con su propietario y restringir el acceso a sus propios registros.

## Autor

Desarrollado por [karolu5](https://github.com/karolu5).