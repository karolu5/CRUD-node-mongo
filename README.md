# CRUD de Tareas con Node.js, Express y MongoDB + Autenticación JWT

Este proyecto es una **API RESTful** para la gestión de tareas. Permite **crear**, **leer**, **editar** y **eliminar** tareas, con rutas protegidas mediante **autenticación con JWT**. Está construido usando Node.js, Express y MongoDB.

---

## Tecnologías usadas

- **Node.js**
- **Express.js**
- **MongoDB + Mongoose**
- **bcrypt** (hash de contraseñas)
- **jsonwebtoken (JWT)** (autenticación)
- **dotenv** (variables de entorno)
- **express-validator** (validaciones)

---

## Estructura del proyecto

crud-backend/ ├── index.js # Servidor principal ├── .env # Variables de entorno ├── models/ │ ├── tarea.model.js # Modelo de Tarea │ └── usuario.model.js # Modelo de Usuario ├── routes/ │ ├── tarea.routes.js # Rutas protegidas de tareas │ └── auth.routes.js # Rutas públicas de autenticación ├── middleware/ │ ├── authMiddleware.js # Middleware para proteger rutas │ └── errorHandler.js # Middleware para errores ├── package.json └── README.md

---

## Instalación 

1. Clonar el repositorio:
```bash
git clone https://github.com/TU_USUARIO/crud-node-mongo.git
cd crud-node-mongo
Instalar dependencias:
```

```bash
npm install
Configurar archivo .env:
```

```bash
env
MONGO_URI=mongodb://localhost:27017/tareasBD
JWT_SECRET=secreto123
PORT=3000
Ejecutar MongoDB en segundo plano:
```

```bash
mongod
Iniciar el servidor:
```

```bash
npm start
Autenticación (JWT)
Registro
POST /auth/register
```

```bash
json
{
  "email": "usuario@email.com",
  "password": "123456"
}
Login
POST /auth/login
```

```bash
json
{
  "email": "usuario@email.com",
  "password": "123456"
}
Devuelve un token JWT:\
```

```bash
json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI..."
}
Endpoints de Tareas (protegidos)
Todas las rutas requieren el token en el header:
```

```bash
http
Authorization: Bearer TU_TOKEN
```

Método	Ruta	Descripción
GET	/tareas	Obtener todas las tareas
POST	/tareas	Crear nueva tarea
GET	/tareas/:id	Obtener tarea por ID
PUT	/tareas/:id	Actualizar tarea
DELETE	/tareas/:id	Eliminar tarea
Ejemplo de body para POST/PUT:

```bash
json
{
  "texto": "Aprender MongoDB"
}'
```

Funcionalidades

Registro/Login de usuarios

Autenticación con JWT

CRUD completo de tareas

Middleware de errores

Rutas protegidas

Validación de datos

Listo para deploy

Autor

Juan Carlos Chavez – Desarrollador Backend Jr.

Contacto: jcczcom@gmail.com

LinkedIn https://www.linkedin.com/in/karolu5/



