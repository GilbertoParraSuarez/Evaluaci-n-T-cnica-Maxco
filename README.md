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

### 3. Configurar Variables de Entorno

Copia el archivo de configuración de ejemplo:

```bash
cp .env.example .env
```

Edita el archivo `.env` y configura la conexión a la base de datos:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=maxco
DB_USERNAME=tu_usuario
DB_PASSWORD=tu_contraseña
```

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
# Compilar assets en modo desarrollo
npm run dev

# Observar cambios en tiempo real
npm run dev --watch

# Ejecutar servidor de desarrollo
php artisan serve
```

### Base de Datos
```bash
# Ejecutar migraciones
php artisan migrate

# Revertir migraciones
php artisan migrate:rollback

# Refrescar migraciones (CUIDADO: Elimina todos los datos)
php artisan migrate:fresh
```

### Mantenimiento
```bash
# Limpiar cache de aplicación
php artisan cache:clear

# Limpiar cache de configuración
php artisan config:clear

# Limpiar cache de rutas
php artisan route:clear

# Optimizar aplicación para producción
php artisan optimize
```
Màs info: https://deepwiki.com/GilbertoParraSuarez/Maxco/1-maxco-sales-management-system

## Solución de Problemas Comunes

### Error: "The zip extension and unzip/7z commands are both missing"

Solución: Habilita la extensión zip en tu archivo `php.ini`:
```ini
extension=zip
```
Luego reinicia tu servidor web.

### Error de Conexión a la Base de Datos

1. Verifica que MySQL esté ejecutándose
2. Confirma las credenciales en el archivo `.env`
3. Asegúrate de que la base de datos `maxco` existe

### Assets no se Cargan

1. Ejecuta `npm run build` para compilar assets
2. Verifica que el servidor web tenga permisos de lectura en la carpeta `public/`

## Contribución

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -m 'Agregar nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

## Licencia

Este proyecto está licenciado bajo [especificar licencia].

## Soporte

Para reportar bugs o solicitar nuevas funcionalidades, por favor abre un issue en el repositorio del proyecto.
