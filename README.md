# Superheroe Backend
Joel Abisahi Urena Arroyo
23040897

Servicio centralizado para la gestión de superhéroes, desarrollado bajo una arquitectura robusta utilizando el entorno de ejecución **Node.js** y **TypeScript**. Este sistema permite el manejo de catálogos, perfiles de usuario y persistencia de favoritos mediante una base de datos relacional.

---

##  Guía

Sigue estos pasos para configurar el entorno de desarrollo local una vez tengas el código en tu equipo:

### 1. Gestión de Dependencias
Asegúrate de tener Node.js instalado y ejecuta el siguiente comando para instalar los módulos necesarios:

```bash
npm install
```

### 2. Configuración del Env
Es indispensable definir las variables de entorno para la conectividad. Crea un archivo denominado `.env` en el directorio raíz con el siguiente esquema:

```env
DATABASE_URL=postgres://usuario:password@localhost:5432/superheroedb
JWT_SECRET=tu_llave_maestra
PORT=3000
```

### 3. Preparación de la Base de Datos
Para inicializar el esquema y los datos de prueba, utiliza el motor de migraciones Knex incluido en el proyecto:

```bash
# Ejecutar migraciones pendientes
npx knex migrate:latest

# Cargar datos iniciales (Seeds)
npm run seed
```

### 4. Lanzamiento del Servidor
Para iniciar el servicio en modo de desarrollo con recarga automática (hot-reload):

```bash
npm run dev
```

---

## 📑 Documentación de la API

### Módulo de Autenticación (`/api/auth`)
| Método | Endpoint | Funcionalidad | Requiere Token |
| :--- | :--- | :--- | :---: |
| `POST` | `/register` | Crea una nueva cuenta de usuario. | No |
| `POST` | `/login` | Valida credenciales y entrega Token JWT. | No |
| `GET` | `/profile` | Obtiene la información del usuario autenticado. | Sí |

### Módulo de Héroes (`/api/heroes`)
| Método | Endpoint | Funcionalidad | Requiere Token |
| :--- | :--- | :--- | :---: |
| `GET` | `/catalog` | Recupera la lista global de héroes. | No |
| `GET` | `/catalog/:id` | Muestra la ficha detallada de un héroe. | No |
| `GET` | `/favorites` | Lista de héroes marcados por el usuario. | Sí |
| `POST` | `/favorites` | Vincula un héroe a la lista de favoritos. | Sí |
| `DELETE` | `/favorites/:heroId` | Remueve un héroe de la lista de favoritos. | Sí |

---

## 🛠 Stack Tecnológico
* **Runtime:** Node.js con TypeScript.
* **Framework:** Express.js.
* **ORM/Query Builder:** Knex.js & Objection.js.
* **Database:** PostgreSQL.
* **Seguridad:** Bcryptjs (hashing) y JSON Web Tokens (sesiones).
* **Utilidades:** Morgan (logging de peticiones).
