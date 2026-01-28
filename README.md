# AvanceDFS - Aplicación Full Stack de Notas y Pendientes

## Descripción del Proyecto

Esta aplicación full stack permite a los usuarios gestionar notas personales y listas de pendientes (todos) con autenticación de usuarios. Está orientada a sectores de interés amplio, como educativo, personal o productivo, facilitando la organización de información y tareas.

En la primera fase del reto, los aprendedores deberán crear la base de una aplicación full stack con un enfoque general y de interés amplio (puede estar orientada a sectores como el educativo, automotriz, financiero, industrial, etc.), y centrarse en el desarrollo del frontend y backend utilizando Node.js y Express.js. Esta fase incluye la configuración del servidor, la implementación de rutas y middleware, y la gestión de operaciones CRUD en una base de datos. Además, se espera la creación de un diseño básico de interfaz utilizando HTML, CSS y JavaScript.

### Características Principales
- **Autenticación de Usuarios**: Registro y login con JWT.
- **Gestión de Notas**: Crear, leer y almacenar notas personales.
- **Gestión de Pendientes**: Crear, leer y gestionar listas de tareas.
- **Interfaz Web**: Frontend simple con HTML, CSS y JavaScript vanilla.
- **Base de Datos**: MongoDB para persistencia de datos.

## Tecnologías Utilizadas
- **Backend**: Node.js, Express.js, MongoDB con Mongoose, JWT para autenticación, bcrypt para hashing de contraseñas.
- **Frontend**: HTML, CSS, JavaScript (vanilla).
- **Herramientas**: Nodemon para desarrollo, dotenv para variables de entorno.

## Estructura del Proyecto

```
AvanceDFS/
├── backend/                          # Carpeta del backend
│   ├── .env                          # Variables de entorno (JWT_SECRET, MONGODB_URI, PORT)
│   ├── package.json                  # Dependencias y scripts de Node.js
│   ├── package-lock.json             # Lockfile de npm
│   └── src/                          # Código fuente del backend
│       ├── app.js                    # Configuración principal de Express (middlewares, rutas)
│       ├── server.js                 # Punto de entrada del servidor
│       ├── config/
│       │   └── db.js                 # Conexión a MongoDB
│       ├── middleware/
│       │   ├── authMiddleware.js     # Middleware para verificar JWT
│       │   └── errorHandler.js       # Middleware para manejo de errores
│       ├── models/
│       │   └── User.js               # Modelo de usuario con esquemas de notas y todos
│       └── routes/
│           ├── auth.js               # Rutas de autenticación (register, login)
│           ├── notes.js              # Rutas CRUD para notas
│           └── todos.js              # Rutas CRUD para pendientes
├── frontend/                         # Carpeta del frontend
│   ├── index.html                    # Página principal con formularios de login, notas y todos
│   ├── styles.css                    # Estilos CSS para la interfaz
│   └── app.js                        # Lógica JavaScript para interactuar con la API
└── users.json                        # Archivo JSON (datos de ejemplo)
```

### Descripción Detallada de Carpetas y Archivos
- **backend/**: Contiene todo el código del servidor. Usa Express para manejar rutas, MongoDB para datos, y JWT para sesiones.
- **frontend/**: Interfaz de usuario simple. `index.html` define la estructura, `styles.css` el diseño, y `app.js` maneja las interacciones con el backend vía fetch API.
- **users.json**: Archivo JSON que podría contener datos de usuarios de ejemplo o ser un remanente; no se usa en el código actual.

## Prerrequisitos
- Node.js (versión 14 o superior)
- MongoDB (instancia local o en la nube, e.g., MongoDB Atlas)
    - Base de datos: `notas_app`
    - Colección: `users`
- Un cliente HTTP como Thunder Client (extensión de VS Code) o Postman para probar la API.

## Instalación y Configuración

1. **Clonar el repositorio** (si está en Git):
   ```
   git clone <url-del-repositorio>
   cd AvanceDFS
   ```

2. **Configurar el Backend**:
   - Navega a la carpeta `backend`:
     ```
     cd backend
     ```
   - Instala las dependencias:
     ```
     npm install
     ```
   - Configura las variables de entorno en `.env`:
     - `PORT=4000` (puerto del servidor)
     - `MONGODB_URI=mongodb://127.0.0.1:27017/notas_app` (URI de MongoDB)
     - `JWT_SECRET=tu_clave_secreta_aqui` (clave secreta para JWT, cámbiala por algo seguro)

3. **Configurar el Frontend**:
   - El frontend no requiere instalación adicional, ya que es estático. Solo asegúrate de que el backend esté corriendo.

4. **Ejecutar el Proyecto**:
   - Inicia el servidor backend:
     ```
     npm run dev
     ```
     Esto iniciará el servidor en `http://localhost:4000`.
   - Abre `frontend/index.html` en un navegador web para acceder a la aplicación.

## Uso

### Registro de Usuario
Para registrar un nuevo usuario, usa un cliente HTTP como Thunder Client:

1. Abre Thunder Client en VS Code.
2. Crea una nueva solicitud:
   - Método: `POST`
   - URL: `http://localhost:4000/api/auth/register`
   - Headers: `Content-Type: application/json`
   - Body (JSON):
     ```json
     {
       "name": "Nombre del Usuario",
       "email": "usuario@example.com",
       "password": "contraseña_segura"
     }
     ```
3. Envía la solicitud. Deberías recibir una respuesta 201 con los datos del usuario (sin la contraseña).

### Inicio de Sesión
- Abre `frontend/index.html` en el navegador.
- Ingresa email y contraseña en el formulario de login.
- Si es correcto, accederás a la sección de notas y pendientes.

### Gestión de Notas y Pendientes
- Una vez logueado, puedes agregar notas (título y contenido) y pendientes (título).
- Las notas y todos se cargan automáticamente desde la API.

## Endpoints de la API

### Autenticación
- `POST /api/auth/register`: Registrar un nuevo usuario.
- `POST /api/auth/login`: Iniciar sesión y obtener token JWT.

### Notas
- `GET /api/notes`: Obtener notas del usuario (requiere token).
- `POST /api/notes`: Crear una nueva nota (requiere token).

### Pendientes
- `GET /api/todos`: Obtener pendientes del usuario (requiere token).
- `POST /api/todos`: Crear un nuevo pendiente (requiere token).

Todos los endpoints protegidos requieren el header `Authorization: Bearer <token>`.

## Contribución
- Realiza un fork del repositorio.
- Crea una rama para tus cambios o toma el proyecto de ejemplo.
- Sigue las instrucciones de tu avance del proyecto.

## Licencia
Este proyecto es para fines educativos y puedes utilizarlo, analizarlo y modificarlo.
