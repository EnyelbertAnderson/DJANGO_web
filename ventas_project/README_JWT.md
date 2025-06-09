# Configuración de Autenticación JWT en Django REST Framework

Este instructivo te guía paso a paso para implementar autenticación mediante JSON Web Token (JWT) en tu proyecto Django.

## 1. Instalar dependencias

Abre la terminal en la carpeta del proyecto y ejecuta:

```
pip install djangorestframework-simplejwt
```

## 2. Configurar Django REST Framework para usar JWT

Edita el archivo `ventas_project/settings.py` y reemplaza la configuración de autenticación por defecto por la de JWT:

```python
REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.IsAuthenticated',
    ],
}
```

## 3. Agregar las rutas de JWT al proyecto

Edita el archivo `ventas/urls.py` y agrega:

```python
from rest_framework_simplejwt.views import (
    TokenObtainPairView,
    TokenRefreshView,
)

urlpatterns += [
    path('jwt/create/', TokenObtainPairView.as_view(), name='token_obtain_pair'),
    path('jwt/refresh/', TokenRefreshView.as_view(), name='token_refresh'),
]
```

## 4. Migraciones (si es necesario)

No se requieren migraciones adicionales para JWT.

## 5. Cómo obtener y usar el token JWT

### Obtener el token

Haz un POST a `/api/jwt/create/` con tu usuario y contraseña:

```
POST http://127.0.0.1:8000/api/jwt/create/
Content-Type: application/json

{
  "username": "tu_usuario",
  "password": "tu_contraseña"
}
```

La respuesta será:
```
{
  "refresh": "<refresh_token>",
  "access": "<access_token>"
}
```

### Usar el token

En cada petición protegida, agrega el header:
```
Authorization: Bearer <access_token>
```

### Refrescar el token

Haz un POST a `/api/jwt/refresh/` con el refresh token:

```
POST http://127.0.0.1:8000/api/jwt/refresh/
Content-Type: application/json

{
  "refresh": "<refresh_token>"
}
```

## 6. Notas
- Elimina o comenta la autenticación por Token si solo usarás JWT.
- Puedes seguir usando el admin de Django con tu usuario superusuario.

---
¡Listo! Ahora tu API usa autenticación JWT estándar.
