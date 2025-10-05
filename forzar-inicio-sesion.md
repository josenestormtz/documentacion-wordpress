# 🔒 WordPress – Forzar inicio de sesión con redirección personalizada

Este mini tutorial explica cómo usar el plugin **Force Login** para convertir un sitio WordPress en una intranet privada, redirigiendo a los usuarios no autenticados a una página personalizada.

---

## 🚀 Requisitos

- WordPress instalado y funcionando.
- Acceso de administrador al panel.
- (Opcional) Editor de código o plugin **Code Snippets**.

---

## 🧩 Paso 1. Instalar el plugin

1. En el panel de administración, ir a **Plugins → Añadir nuevo**.  
2. Buscar **Force Login** (desarrollado por Kevin Vess).  
3. Hacer clic en **Instalar** y luego **Activar**.

El sitio ahora será accesible **solo para usuarios con sesión iniciada**.  
Los visitantes anónimos serán redirigidos al login estándar de WordPress (`/wp-login.php`).

---

## ⚙️ Paso 2. Agregar la redirección personalizada

Para enviar a los usuarios no autenticados a una URL diferente (por ejemplo, una página de login personalizada o portal externo), añade el siguiente fragmento de código en tu tema hijo o mediante el plugin **Code Snippets**:

```php
/**
 * Personalizar la URL de redirección de Force Login
 * Redirige a usuarios no autenticados a una página específica
 */
add_filter( 'v_forcelogin_redirect', function( $redirect_to ) {
    // Cambia esta URL por la de tu página personalizada
    return 'https://tusitio.com/pagina-de-login';
});
```

🧠 Ejemplo avanzado (redirigir según rol)
```php
add_filter( 'v_forcelogin_redirect', function( $redirect_to ) {
    if ( current_user_can('administrator') ) {
        return 'https://tusitio.com/admin-area';
    } else {
        return 'https://tusitio.com/login-empleados';
    }
});
```

✅ Resultado
Los usuarios sin sesión activa serán redirigidos automáticamente a la URL especificada.
Los usuarios logueados accederán normalmente a todo el sitio.

Este método es ideal para crear intranets, portales internos o entornos de prueba privados con WordPress.
