# 📦 MicroServiciosProductosInventario

Proyecto técnico con arquitectura de microservicios en .NET 6. Incluye dos servicios:

- `Productos.API`: Gestión de productos.
- `Inventario.API`: Gestión del inventario con autenticación por API Key.

Ambos se comunican por HTTP y están contenedorizados con Docker. Usa SQL Server como base de datos.

---

## 📁 Estructura del Proyecto

```
MicroServiciosProductosInventario/
├── docker-compose.yml
├── Productos.API/
├── Inventario.API/
├── SqlScripts/
└── README.md
```

---

## 🧰 Tecnologías Usadas

- .NET 6
- SQL Server
- Docker y Docker Compose
- JSON API
- Swagger
- API Key Authentication (solo para Inventario)
- Pruebas unitarias (xUnit)
- Comunicación HTTP entre servicios

---

## 🚀 Instrucciones de Ejecución

### 1. Requisitos previos

- Visual Studio 2022 o VS Code
- Docker Desktop en ejecución
- Puertos `59485` (productos) y `59486` (inventario) disponibles

### 2. Clonar o descargar el proyecto

```bash
git clone https://github.com/nestormauricio/MicroServiciosProductosInventario.git
cd MicroServiciosProductosInventario

📬 Ejemplo de flujo de compra
POST /api/compras
Host: localhost:6002
X-API-KEY: 12345-API-KEY
Content-Type: application/json

{
  "productoId": 1,
  "cantidad": 2
}



> ⚠️ Usa la API Key: `12345-API-KEY` en los headers para el servicio de Inventario.


## 🧪 Pruebas

Ejecuta las pruebas con:

```bash
dotnet test
```

---

## 📬 Ejemplo de flujo de compra

```http
POST /api/compras
Host: localhost:6002
X-API-KEY: 12345-API-KEY
Content-Type: application/json

{
  "productoId": 1,
  "cantidad": 2
}
```

**Respuesta esperada**:

```json
{
  "mensaje": "Compra realizada. Stock actualizado."
}
```

---

## 📂 Datos precargados

Al ejecutar `docker-compose`, se insertan automáticamente:

- 5 productos en `Productos.API`
- 5 registros de inventario en `Inventario.API`

---

## 📄 Autenticación

- Microservicio `Inventario.API` requiere header: `X-API-KEY: 12345-API-KEY`
- Middleware personalizado implementado en `Inventario.API/Middleware`

---

## 🧩 Arquitectura

- Comunicación entre servicios por HTTP
- Separación de responsabilidades
- Servicios independientes y desplegables

---

## ❓ Solución de problemas

- ❌ **Error al conectar con SQL Server**:
  - Asegúrate de que Docker esté corriendo
  - Puerto 1433 no esté ocupado
- ❌ **Faltan paquetes NuGet**:
  - Ejecuta `dotnet restore` o usa el gestor de paquetes en Visual Studio
- ❌ **API Key inválida**:
  - Verifica que estés usando `X-API-KEY: 12345-API-KEY`

---

## 👨‍💻 Autor

Desarrollado por [Nestor Mauricio Pérez Ruíz - nestormauricio@live.com - +573107760510]
