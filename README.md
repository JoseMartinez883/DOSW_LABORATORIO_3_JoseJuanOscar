# Laboratorio 3: Requerimientos, UML, Agile Scrum y Jira
**Materia:** Desarrollo de Operaciones de Software (DOWS)
**Institución:** Escuela Colombiana de Ingeniería Julio Garavito

## Equipo de Trabajo
* Oscar Lasso 
* Juan Diego Gaitan
* Jose Martinez

### CONCEPTO DEL RESTAURANTE: ITALIANO

#### REGLAS DE NEGOCIO DEL SISTEMA

**Reglas Generales:**
1. **Bloqueo de Modificación:** Un pedido solo puede modificarse mientras esté en estado `RECIBIDO`. Una vez pasa a `EN PREPARACIÓN`, la cocina ya lo tomó y no admite cambios.
2. **Disponibilidad por Inventario:** Un plato no puede ordenarse si alguno de sus ingredientes está agotado: el sistema lo marca como *no disponible* automáticamente.
3. **Cuentas por Mesa:** Una mesa solo puede tener una cuenta abierta a la vez; la cuenta se cierra únicamente cuando el pago queda registrado.
4. **Congelamiento de Precios:** El precio de un plato queda congelado en el momento en que se agrega al pedido, aunque después cambie en la carta.

**Reglas Propias (Concepto Italiano):**
1. **Límite de Toppings (Pizza):** Una pizza no puede llevar más de 5 toppings en total.
2. **Construcción Estricta (Pizza/Pasta):** Todo plato personalizable debe tener obligatoriamente registrada una *masa base* (o tipo de pasta) y una *salsa primaria* antes de permitir la adición de cualquier topping.
3. **Límite de Proteínas (Pasta):** Un plato de pasta puede contener un máximo de 2 proteínas en su base.
4. **Límite de Salsas (Pasta):** Un plato de pasta puede tener un máximo de 3 tipos de salsas combinadas.

## Objetivo
Aplicar herramientas de definición y análisis de requerimientos a partir de un caso de estudio práctico, y herramientas de planeación usando el framework Agile Scrum con Jira. El sistema que definan aquí será la base del proyecto de API que construirán durante el segundo corte.

## Gestión de Versiones con GitHub

### ¿Qué es un pull request en GitHub?
Un pull request es una solicitud formal en GitHub que un desarrollador crea para proponer la incorporación de cambios de código desde una rama de trabajo hacia otra rama base. Actúa como un espacio de revisión colaborativa donde los miembros del equipo pueden examinar las diferencias de código, discutir modificaciones, ejecutar pruebas automáticas y asegurar el cumplimiento de estándares antes de fusionar con un merge el código de forma definitiva en el proyecto base.

### ¿Cómo se crea un pull request en GitHub?
Para crear un pull request se deben seguir los siguientes pasos básicos:
1. Publicar haciendo *push* de la rama local con los nuevos commits al repositorio remoto en GitHub.
2. Ingresar a la página principal del repositorio en GitHub.
3. Hacer clic en la pestaña **Pull requests** y luego en el botón verde **New pull request** 
4. Seleccionar la rama base en el menú desplegable "base", y la rama de comparación en el menú "compare".
5. Asignar un título descriptivo y agregar una descripción detallando los cambios realizados, el contexto y cualquier información relevante para los revisores.
6. Hacer clic en **Create pull request**.

### ¿Cómo se aprueba un pull request en GitHub?
La aprobación de un pull request es un proceso de revisión por pares que asegura la calidad del software:
1. Un revisor ingresa al pull request desde la pestaña **Pull requests** del repositorio.
2. Hace clic en la pestaña **Files changed** para examinar las líneas de código específicas que fueron modificadas, agregadas o eliminadas.
3. Tras la verificación, hace clic en el botón verde **Review changes** ubicado en la parte superior derecha de esa sección.
4. Selecciona la opción **Approve** e incluye un comentario general validando la revisión.
5. Haz clic en **Submit review**. Una vez que el pull request cuenta con las aprobaciones necesarias, se habilitará el botón **Merge pull request** para que los cambios se integren oficialmente.

## Bibliografía
GitHub. (s.f.). *Acerca de las solicitudes de incorporación de cambios*. GitHub Docs. Recuperado el 27 de agosto de 2026, de https://docs.github.com/es/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests

GitHub. (s.f.). *Crear una solicitud de incorporación de cambios*. GitHub Docs. Recuperado el 27 de agosto de 2026, de https://docs.github.com/es/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request

GitHub. (s.f.). *Revisar los cambios propuestos en una solicitud de incorporación de cambios*. GitHub Docs. Recuperado el 27 de agosto de 2026, de https://docs.github.com/es/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request
