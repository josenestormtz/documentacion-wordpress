# Ocultar dirección de facturación en WooCommerce

## 📋 Descripción
Por defecto, WooCommerce muestra la **dirección de facturación** en la página de **“Gracias por tu pedido”**.  
Este snippet de CSS permite **ocultar visualmente la dirección de facturación** para que solo se muestre la dirección de envío.

---

## ⚙️ Instrucciones

1. Ve a **Apariencia → Personalizar → CSS adicional** en tu panel de WordPress.  
2. Copia y pega el siguiente CSS:

```css
/* Ocultar dirección de facturación en la página de gracias por tu pedido */
.woocommerce-customer-details {
    display: none;
}
```

Guarda los cambios y refresca la página de “Gracias por tu pedido” para verificar que la dirección de facturación ya no se muestre.

🏁 Resultado esperado

Antes:

Dirección de facturación + Dirección de envío

Después:

Solo la dirección de envío
