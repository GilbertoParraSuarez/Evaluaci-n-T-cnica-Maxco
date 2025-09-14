# Maxco - Sistema de Gestión de Ventas
Maxco es una plataforma integral de gestión de ventas desarrollada con Laravel y Vue.js que maneja todo el ciclo de vida de ventas empresariales, incluyendo gestión de clientes, proveedores, productos, territorios y procesamiento de transacciones con inventario en tiempo real.
## Tecnologías Utilizadas
- **Backend**: Laravel 12.x
- **Frontend**: Vue.js 3 con Inertia.js
- **Base de Datos**: MySQL
- **Autenticación**: Laravel Sanctum
- **Herramientas de Desarrollo**: Laravel Pint, PHPUnit, Collision
## Arquitectura del Sistema
El sistema sigue una arquitectura de tres niveles con clara separación entre:
- **Capa de Presentación**: Vue.js 3 con Inertia.js
- **Capa de Aplicación**: Laravel MVC
- **Capa de Datos**: MySQL con Eloquent ORM
### Dominios de Negocio
1. **Ventas** - Hub central que integra todos los demás dominios
2. **Clientes** - Gestión de relaciones con clientes
3. **Proveedores** - Administración de proveedores
4. **Productos** - Catálogo, precios e inventario
5. **Zonas** - Gestión territorial
6. **Analytics** - Reportes e inteligencia de negocio
## Requisitos Previos
- PHP 8.2 o superior
- Composer
- Node.js 18+ y npm
- MySQL 8.0 o superior
- Servidor web (Apache/Nginx) o usar el servidor integrado de PHP
### Extensiones PHP Requeridas
Asegúrate de tener habilitadas las siguientes extensiones en tu `php.ini`:
- `extension=zip` (requerida para Composer)
- `extension=pdo_mysql`
- `extension=mbstring`
- `extension=openssl`
- `extension=tokenizer`
- `extension=xml`
- `extension=ctype`
- `extension=json`
## Instalación
### 1. Clonar el Repositorio
```bash
git clone <url-del-repositorio>
cd maxco
```
### 2. Configurar la Base de Datos
Crea una base de datos MySQL con el nombre `maxco`:
```sql
CREATE DATABASE maxco CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```
### 3. Crear el Archivo `.env`
El sistema requiere un archivo de configuración `.env` que contenga las variables necesarias para correr el proyecto. Copia el archivo de ejemplo incluido en el repositorio:
```bash
cp .env.example .env
```
El archivo `.env` debe contener los mismos parámetros que `.env.example`. Asegúrate de editarlo para configurar correctamente la conexión a la base de datos:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=maxco
DB_USERNAME=tu_usuario
DB_PASSWORD=tu_contraseña
```
>**Nota importante**: El proyecto no funcionará sin este archivo `.env`. Por defecto, `.env.example` incluye todas las variables necesarias, por lo que basta con copiarlo y ajustar los valores correspondientes.
### 4. Instalar Dependencias de PHP
```bash
composer install
```
**Nota**: Si encuentras errores relacionados con extensiones zip faltantes, asegúrate de habilitar la extensión zip en tu `php.ini`:
```ini
extension=zip
```
### 5. Instalar Dependencias de JavaScript
```bash
npm install
```
### 6. Generar Clave de Aplicación
```bash
php artisan key:generate
```
### 7. Ejecutar Migraciones
```bash
php artisan migrate
```
### 8. Compilar Assets (Desarrollo)
```bash
npm run dev
```
Para producción:
```bash
npm run build
```
## Ejecutar el Proyecto
### Servidor de Desarrollo
```bash
php artisan serve
```
El proyecto estará disponible en: `http://localhost:8000`
### Desarrollo con Hot Reload
En una terminal separada, ejecuta:
```bash
npm run dev
```
Esto habilitará la recarga automática de los assets durante el desarrollo.
## Estructura del Proyecto
```
maxco/
├── app/
│   ├── Http/Controllers/        # Controladores del sistema
│   │   ├── SalesController.php  # Controlador principal de ventas
│   │   ├── CustomersController.php
│   │   ├── VendorsController.php
│   │   ├── ProductsController.php
│   │   └── ZonesController.php
│   └── Models/                  # Modelos Eloquent
├── resources/
│   ├── js/
│   │   ├── Layouts/
│   │   │   └── AuthenticatedLayout.vue  # Layout principal
│   │   └── Pages/               # Páginas Vue.js
│   └── views/
├── routes/
│   └── web.php                  # Rutas del sistema
├── database/
│   └── migrations/              # Migraciones de base de datos
└── public/                      # Assets públicos compilados
```
## Características Principales
- **Gestión Integral de Ventas**: Procesamiento completo del ciclo de ventas
- **Gestión de Inventario**: Control de stock en tiempo real
- **Múltiples Entidades**: Clientes, proveedores, productos, zonas
- **Interfaz Moderna**: SPA con Vue.js 3 e Inertia.js
- **Autenticación Segura**: Sistema de roles basado en Laravel
- **Reportes y Analytics**: Dashboard con inteligencia de negocio
## Comandos Útiles
### Desarrollo
```bash
npm run dev          # Compilar assets en modo desarrollo
npm run dev --watch  # Observar cambios en tiempo real
php artisan serve    # Ejecutar servidor de desarrollo
```
### Base de Datos
```bash
php artisan migrate          # Ejecutar migraciones
php artisan migrate:rollback # Revertir migraciones
php artisan migrate:fresh    # Refrescar migraciones (CUIDADO: elimina todos los datos)
```
### Mantenimiento
```bash
php artisan cache:clear   # Limpiar cache de aplicación
php artisan config:clear  # Limpiar cache de configuración
php artisan route:clear   # Limpiar cache de rutas
php artisan optimize      # Optimizar aplicación para producción
```
Màs info: [Documentación en Deepwiki](https://deepwiki.com/GilbertoParraSuarez/Maxco/1-maxco-sales-management-system)
