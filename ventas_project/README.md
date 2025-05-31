# Ventas Project

Este es un proyecto Django para la gestión de ventas.

## Estructura del proyecto
- `ventas_project/`: Configuración principal del proyecto Django.
- `ventas/`: Aplicación principal donde se encuentran los modelos, vistas, serializadores y pruebas.

## Requisitos
- Python 3.13 o compatible
- Django (versión recomendada: 4.x o superior)

## Instalación
1. Clona este repositorio.
2. Instala las dependencias:
   ```powershell
   pip install django
   ```
3. Realiza las migraciones:
   ```powershell
   python manage.py migrate
   ```
4. Ejecuta el servidor de desarrollo:
   ```powershell
   python manage.py runserver
   ```

## Uso
Accede a `http://127.0.0.1:8000/` para ver la aplicación en funcionamiento.

## Estructura de carpetas
- `ventas/`: Contiene la lógica de la aplicación (modelos, vistas, urls, etc).
- `ventas_project/`: Configuración global del proyecto.

## Licencia
Este proyecto es solo para fines educativos.
