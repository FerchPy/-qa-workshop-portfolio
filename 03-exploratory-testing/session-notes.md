# Sesión 1

## Charter
Explorar la gestión del carrito de compras en la PetStore, usando cambios de estado y combinaciones de acciones (agregar, eliminar, modificar), para descubrir inconsistencias, pérdida de datos y comportamientos inesperados.

## ÁREAS
Carrito de compras – JPetStore

## INICIO
22/04/2026 – (Duración: 45 minutos)

## TESTER
José Fernando Paniagua Benitez

## DESGLOSE DE TAREAS
- 25 min: Agregar productos al carrito desde distintas categorías (logueado y sin sesión)
- 10 min: Modificar cantidades y eliminar productos
- 10 min: Navegación, persistencia del carrito y validaciones límite

## ARCHIVOS DE DATOS
Productos del catálogo de la JPetStore (sin archivos externos)

## NOTAS DE PRUEBA
Se intentó agregar el producto Large Angelfish (EST-1, FI-SW-01, $16.50) desde el catálogo haciendo clic en "Add to Cart". El sistema redirigió al carrito pero el producto no fue agregado — el carrito apareció vacío con Sub Total $0.00.

Se repitió la misma acción con el producto Poodle (EST-8, K9-PO-02, $18.50). El comportamiento fue idéntico: redirección al carrito sin que el ítem aparezca.

Se probó el flujo tanto sin sesión iniciada como logueado con usuario registrado. El problema persiste en ambos casos, descartando que sea un problema de autenticación.

Se modificó la cantidad de un producto en el carrito ingresando el valor 0. El producto desapareció del carrito sin mostrar ningún mensaje de advertencia ni solicitar confirmación al usuario.

Se repitió la prueba ingresando valores negativos (ej. -1). El comportamiento fue el mismo: el producto se elimina silenciosamente sin validación visible.

Se agregó un producto al carrito con sesión iniciada, luego se cerró sesión. Al volver a iniciar sesión, el carrito apareció vacío — el contenido no persiste entre sesiones.

## LISTA DE RIESGOS
- El flujo principal de compra está roto: los productos no se agregan al carrito
- Eliminación silenciosa de productos al ingresar cantidad 0 o negativa, sin advertencia
- El carrito no persiste al cerrar sesión, lo que puede generar frustración y abandono

## DEFECTOS (BUGS)

**Bug 1: "Add to Cart" no agrega el producto al carrito**
- **Productos afectados:** Large Angelfish (EST-1), Poodle (EST-8) — comportamiento general, no aislado a un producto
- **Pasos para reproducir:** Navegar al catálogo → seleccionar cualquier producto → hacer clic en "Add to Cart"
- **Resultado esperado:** El producto aparece en el carrito con cantidad 1 y el subtotal se actualiza
- **Resultado actual:** El sistema redirige a la página del carrito pero este aparece vacío ("Your cart is empty", Sub Total: $0.00)
- **Condiciones probadas:** Sin sesión iniciada y logueado — el bug ocurre en ambos casos
- **Impacto:** Alto – el flujo principal de compra no funciona

**Bug 2: Cantidad 0 o negativa elimina el producto sin advertencia**
- **Pasos para reproducir:** Tener un producto en el carrito → modificar la cantidad a 0 o un valor negativo → presionar "Update Cart"
- **Resultado esperado:** El sistema debería mostrar un mensaje de validación e impedir la acción
- **Resultado actual:** El producto desaparece del carrito de forma inmediata y silenciosa
- **Impacto:** Medio – puede causar pérdida accidental de productos del carrito

## INCIDENTES (ISSUES)
- El carrito no persiste al cerrar sesión: no está claro si es comportamiento esperado o un defecto. No hay documentación ni criterio definido al respecto.