# 🔐 API REST — Usuarios e Items

API REST con **Node.js + Express + MongoDB** que implementa autenticación con JWT, control de roles, subida de imágenes a Cloudinary y operaciones CRUD sobre dos recursos relacionados (usuarios ↔ items).

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=flat&logo=jsonwebtokens&logoColor=white)

---

## ✨ Funcionalidades

- 👤 Registro e inicio de sesión con **JWT** (con expiración) y contraseña **hasheada (bcrypt)**
- 🛡️ Middleware de **autenticación** y de **rol admin**
- 🖼️ Subida de imagen de perfil a **Cloudinary** (stream en memoria con Multer)
- 📦 CRUD de items y relación usuario → items
- 🔒 Las respuestas **nunca exponen el hash** de la contraseña

---

## 🛠️ Stack técnico

| Tema | Detalle |
|------|---------|
| Runtime | Node.js · Express |
| Base de datos | MongoDB · Mongoose |
| Auth | JWT · bcrypt |
| Media | Cloudinary · Multer |

---

## 🗂️ Estructura

```
src/
├── app.js              # Arranque + conexión a MongoDB
├── controllers/        # Lógica de User e Item
├── middleware/         # Auth (JWT + isAdmin) y Upload (Cloudinary)
├── models/             # Esquemas Mongoose
├── routes/             # Rutas REST
└── seed.js             # Datos de prueba
```

---

## 🚀 Puesta en marcha local

```bash
git clone https://github.com/GabiLuke/items-Users.git
cd items-Users
npm install
```

`.env`
```env
MONGO_URI=tu_uri_de_mongodb
JWT_SECRET=tu_secret
CLOUDINARY_URL=cloudinary://api_key:api_secret@cloud_name
PORT=3000
```

```bash
npm run seed   # opcional: carga items de ejemplo
npm run dev    # http://localhost:3000
```

---

## 📡 Endpoints principales

| Método | Ruta | Auth | Descripción |
|--------|------|------|-------------|
| `POST` | `/users/register` | — | Registro (con imagen opcional) |
| `POST` | `/users/login` | — | Login → devuelve JWT |
| `GET` | `/users` | admin | Listar usuarios (sin contraseñas) |
| `PATCH` | `/users/:id/role` | admin | Cambiar rol |
| `DELETE` | `/users/:id` | auth | Eliminar (propietario o admin) |
| `GET/POST` | `/items` | — | Listar / crear items |
| `PUT/DELETE` | `/items/:id` | — | Actualizar / eliminar item |

---

## 🎯 Qué demuestra este proyecto

- Diseño de una **API REST** con recursos relacionados y códigos de estado correctos.
- **Seguridad**: hash de contraseñas, JWT con expiración, control de acceso por rol y no exponer datos sensibles.
- Integración de subida de ficheros a un servicio externo mediante streams.

---

## 👤 Autor

**Gabriel Luque Velasco** — Desarrollador Full-Stack Junior
[GitHub](https://github.com/GabiLuke) · [LinkedIn](#) · gabiluke99@gmail.com
