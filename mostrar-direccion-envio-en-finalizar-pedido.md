# Mostrar dirección de envío en WooCommerce en lugar de facturación

## 📋 Descripción
Por defecto, WooCommerce muestra la **dirección de facturación** en la página de **“Gracias por tu pedido”**.  
Este snippet reemplaza esa información y muestra **la dirección de envío** del cliente.

---

## ⚙️ Instrucciones

1. Instala y activa el plugin **Code Snippets** o usa tu **tema hijo**.  
2. Crea un nuevo snippet y copia el siguiente código PHP:

```php
add_action( 'woocommerce_order_details_after_order_table', 'mostrar_direccion_envio', 10, 1 );

function mostrar_direccion_envio( $order ) {
    if ( ! $order instanceof WC_Order ) return;

    echo '<h2>Dirección de envío</h2>';
    echo '<p>';
    echo $order->get_shipping_first_name() . ' ' . $order->get_shipping_last_name() . '<br>';
    echo $order->get_shipping_address_1() . '<br>';
    if ( $order->get_shipping_address_2() ) echo $order->get_shipping_address_2() . '<br>';
    echo $order->get_shipping_city() . ', ' . $order->get_shipping_state() . '<br>';
    echo $order->get_shipping_postcode() . '<br>';
    echo $order->get_shipping_country();
    echo '</p>';
}
