# Coverage Decisions

## Riesgos que se probarán primero
1. El usuario podría ser cobrado, pero no recibir confirmación de compra
2. El sistema podría permitir comprar productos sin stock disponible
3. Información sensible podría enviarse sin cifrado
4. Mensajes de error poco claros podrían generar abandono de compra

## ¿Por qué esos riesgos son prioridad?
Estos riesgos fueron priorizados debido a su alto impacto en el negocio y la experiencia del usuario. 
Los riesgos relacionados con pagos y seguridad pueden generar pérdidas económicas, reclamos y afectar la confianza del cliente.
Asimismo, problemas de inventario y usabilidad impactan directamente en la conversión de ventas y la satisfacción del usuario.
Por este motivo, se enfocarán primero las pruebas en los flujos críticos de compra, pago, manejo de stock y experiencia del usuario.

## Qué se probará menos o quedará fuera por ahora
- Variaciones menores del diseño visual
- Funcionalidades con bajo uso por parte de los usuarios
- Escenarios extremos poco probables en el cálculo del total del pedido

## Justificación de exclusiones
Estas exclusiones se consideran razonables en una etapa inicial, ya que presentan un menor impacto y menor probabilidad de ocurrencia. 
El esfuerzo de testing se concentra primero en los riesgos críticos que afectan ingresos, seguridad y experiencia de usuario.
Las funcionalidades excluidas podrán ser cubiertas en ciclos posteriores de pruebas.