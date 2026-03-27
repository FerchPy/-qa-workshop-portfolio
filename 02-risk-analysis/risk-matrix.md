# Risk Matrix
| ID | Riesgo | Impacto | Probabilidad | Nivel | Mitigación(Pruebas) |
|----|--------|---------|--------------|-------|---------------|
| R1 | El usuario podría ser cobrado, pero no recibir confirmación de compra | 3 | 5 | 15 | Pruebas end-to-end del flujo de compra, validación de estados del pago, verificación de confirmaciones y notificaciones |
| R2 | El sistema podría permitir comprar productos sin stock disponible | 4 | 4 | 16 | Pruebas funcionales de inventario, escenarios concurrentes de compra, validación de actualización de stock |
| R3 | Información sensible podría enviarse sin cifrado | 2 | 5 | 10 |  Pruebas de seguridad, validación de uso de HTTPS, análisis de tráfico, revisión de configuraciones |
| R4 | Mensajes de error poco claros podrían generar abandono de compra | 4 | 3 | 12 | Pruebas de usabilidad, revisión de mensajes de error, pruebas exploratorias centradas en experiencia de usuario |
| R5 | Error en el cálculo del total del pedido | 2 | 3 | 6 | Pruebas funcionales de precios, impuestos, descuentos y reglas de negocio |