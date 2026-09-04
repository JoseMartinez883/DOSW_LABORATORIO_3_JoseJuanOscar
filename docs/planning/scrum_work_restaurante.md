# Jerarquía Ágil — Sistema de Gestión del Restaurante
 
## 1. ÉPICA
 
**TÍTULO** BELLA CIAO
 
**Descripción:** Permitir el flujo completo del ciclo de vida de los pedidos en el restaurante italiano, abarcando desde la consulta de la carta digital y personalización de órdenes por el cliente o mesero, hasta la recepción, preparación en cocina y actualización de estados en tiempo real sin el uso de papel.
 
---
 
## 2. FEATURE 1: Permitir la personalización de un pedido
 
**TÍTULO** FEAT-01 — Permitir la personalización de un pedido
 
**Descripción:** Capacidad que permite a los clientes y meseros consultar la carta con disponibilidad en tiempo real, configurar ítems respetando las reglas del concepto y modificar la orden mientras la cuenta se encuentre abierta.
 
### Historia de Usuario 1
 
**TÍTULO** STORY-01 — Personalización y adición de pizzas con toppings configurables
 
**Formato:** COMO cliente, QUIERO armar una pizza seleccionando masa, salsa y hasta 5 toppings, PARA personalizar mi plato según mis preferencias.
 
**Prioridad:** Alta — Es la funcionalidad fundamental del concepto de restaurante italiano y genera valor directo desde el primer día de operación.
 
**Criterios de Aceptación:**
- DADO que la cuenta de la mesa está abierta y la pizza tiene menos de 5 toppings seleccionados, CUANDO el cliente elige un nuevo topping y presiona "Agregar al pedido", ENTONCES el ítem se adiciona a la orden y el total se recalcula automáticamente.
- DADO que una pizza ya cuenta con 5 toppings seleccionados, CUANDO el cliente intenta marcar un sexto topping, ENTONCES el sistema bloquea la selección y despliega el mensaje de regla de negocio: "Límite máximo de 5 toppings alcanzado por pizza".

**Subtareas Técnicas:**
- **SUB-01** — Crear el endpoint API REST para recibir y persistir el ítem configurado.
- **SUB-02** — Implementar la validación en la capa de servicio que verifica la regla de negocio de máximo 5 toppings por pizza.
- **SUB-03** — Diseñar el componente UI para selección de masa, salsa y control de casillas de toppings.
- 

### Historia de Usuario 2
 
**TÍTULO** STORY-02 — Edición y modificación de ítems en estado RECIBIDO
 
**Formato:** COMO cliente o mesero, QUIERO modificar cantidades o eliminar ítems de un pedido en estado RECIBIDO, para corregir equivocaciones antes procesar la orden.
 
**Prioridad:** Alta — Evita desperdicio de insumos en cocina y reduce reclamos de clientes.
 
**Criterios de Aceptación:**
- DADO que el pedido está en estado RECIBIDO, CUANDO se modifica la cantidad de un ítem o se elimina, ENTONCES el sistema actualiza la orden y recalcula el monto total de la cuenta.
- DADO que la cocina cambió el estado del pedido a EN PREPARACIÓN, CUANDO se intenta modificar o eliminar un ítem, entonces el sistema deshabilita la opción y muestra "El pedido ya está en preparación y no admite cambios".
  
**Subtareas Técnicas:**
- **SUB-04** — Crear el endpoint API REST para actualizar cantidades o retirar ítems.
- **SUB-05** — Implementar la regla de validación de estado en backend para permitir cambios únicamente si `estado == RECIBIDO`.
- **SUB-06** — Construir los controles interactivos de incremento, decremento y eliminación en la vista del resumen del pedido.
---
 
## 3. FEATURE 2: Permitir gestionar tablero digital de control
 
**TÍTULO** FEAT-02 — Permitir gestionar tablero digital de control
 
**Descripción:** Capacidad que otorga visibilidad completa al personal de cocina sobre las comandas entrantes y permite actualizar el estado operativo de los platos en tiempo real.
 
### Historia de Usuario 3
 
**TÍTULO** STORY-03 — Visualización del tablero de comandas en tiempo real
 
**Formato:** COMO personal de cocina, QUIERO ver en una pantalla las ordenes que van llegando ordenadas por hora de ingreso, para organizar y priorizar la preparación de platos.
 
**Prioridad:** Alta — Reemplaza el flujo manual de papel y elimina retrasos por falta de visibilidad entre salón y cocina.
 
**Criterios de Aceptación:**
- DADO que un cliente o mesero confirma un pedido, CUANDO este pasa a estado RECIBIDO, ENTONCES la nueva comanda se refleja en el tablero de cocina en menos de 2 segundos.
- Dado que hay múltiples comandas activas, cuando se renderizan en el tablero de cocina, entonces se organizan cronológicamente en columnas desde la orden más antigua a la más reciente.
- 
**Subtareas Técnicas :**
- **SUB-07** — Crear el endpoint con filtros por estados activos
- **SUB-08** — Configurar la actualización en tiempo real hacia el tablero de cocina.
- **SUB-09** — Diseñar la interfaz de tarjetas para cocina con tiempos transcurridos e indicadores visuales de alerta.
- 
### Historia de Usuario 4
 
**TÍTULO** STORY-04 — Transición y actualización de estados del pedido en cocina
 
**Formato:** COMO cocinero, QUIERO cambiar el estado del pedido de RECIBIDO a EN PREPARACIÓN y luego a LISTO, PARA notificar al personal del avance del servicio.
 
**Prioridad:** Alta — Habilita la trazabilidad requerida del ciclo de vida de la orden.
 
**Criterios de Aceptación:**
- DADO que una orden está en estado RECIBIDO, CUANDO el cocinero presiona "Iniciar Preparación", ENTONCES el estado cambia a EN PREPARACIÓN y el cronómetro de tiempo de cocina inicia.
- DADO que se finaliza la cocción, CUANDO el cocinero presiona "Marcar como Listo", ENTONCES el estado pasa a LISTO y se emite un evento de notificación al mesero.
**Subtareas Técnicas**
  
- **SUB-10** — Crear el endpoint API para procesar las transiciones de estado del pedido.
- **SUB-11** — Registrar la auditoría de cada cambio de estado guardando el ID del usuario, fecha, hora y nuevo estado.
- **SUB-12** — Implementar los botones de acción rápida.



# PLANNING POKER 

## LINK VIDEO

## Preguntas Reflexivas - Planning Poker (Parte 7)

1. **¿Cuál fue la mayor dificultad a la hora de estimar?**
   - Separar el concepto de tiempo de esfuerzo y complejidad a utilidad y valor. Inicialmente tendíamos a pensar en cuántas horas tomaría desarrollar el tablero en tiempo real, en lugar de comparar su nivel de dificultad.

2. **¿Fue fácil llegar a un consenso?**
   - En historias simples el consenso fue directo.Sin embargo, en la historia del tablero de cocina en tiempo real existió debate inicial entre 5 y 8 puntos debido a la incertidumbre técnica de configurarla

3. **¿Cómo resolvieron las discrepancias grandes?**
   - Quien votó más alto explicó sus argumentos tecnicos no vistos por el equipo, lo que permitió escuchar y reconocer sus puntos de vista para llegar al consenso final.
