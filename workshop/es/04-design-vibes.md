<!-- l10n-sync: source-file="workshop/04-design-vibes.md" -->
# Parte 4: Tematización orientada al diseño

---

En esta parte, usarás los ciclos de planificación e implementación de Copilot para diseñar una transformación completa del tema. Este es un enfoque de desarrollo orientado al diseño: empieza con una visión, itera sobre los elementos visuales y deja que Copilot se encargue del trabajo pesado de CSS.

## Tarea 1: Planifica el tema retro

<!-- track:vscode:start -->
Cambia al modo **Plan** en GitHub Copilot Chat.
<!-- track:vscode:end -->

<!-- track:cli:start -->
Usa `/plan` en GitHub Copilot CLI o pulsa **Shift+Tab** hasta que se active el modo Plan.
<!-- track:cli:end -->

Introduce este prompt:

> Quiero transformar esta página en una experiencia completa de arcade retro. Planifica una renovación visual integral que incluya: efectos de líneas de barrido CRT en el fondo, un brillo de neón pulsante en el título, una insignia VS animada con cambios de color en el degradado, una superposición de brillo en las tarjetas de resultados de usuario, animaciones de entrada flotante para los campos, texto de carga que cambie entre verde y morado y efectos de brillo al pasar el cursor sobre los cuadrados de contribuciones. Mantén el fondo oscuro (`#0a0a1a`) y los colores de acento verde (`#5fed83`) y morado (`#8a2be2`). Usa el tema oscuro y la fuente retro Press Start 2P de Google Fonts.

Copilot generará un plan de implementación detallado que abarcará todos los efectos visuales. **No lo aceptes de inmediato**: revisa el plan e itera:

- Sugiere cambios en la duración de las animaciones (por ejemplo, *«Haz que el pulso de neón sea más lento, de unos 3 segundos»*).
- Pregunta por efectos específicos (por ejemplo, *«¿Cómo funcionará la superposición de brillo en las tarjetas?»*).
- Pide que cambie el enfoque si algo no te convence.

## Tarea 2: Implementa el tema

Cuando te convenza el plan, pide a Copilot que lo implemente:

> Implementa el plan del tema de arcade retro que acabamos de diseñar.

Copilot añadirá varias animaciones CSS, pseudoelementos y transiciones a la hoja de estilos. Esto puede incluir:

- `@keyframes` para líneas de barrido, pulsos de neón, brillo y efectos de entrada flotante
- Pseudoelementos (`::before`, `::after`) para efectos de superposición
- Propiedades personalizadas de CSS para los colores del tema
- Transiciones y estados hover para los elementos interactivos

<!-- track:cli:start -->
Cuando terminen los cambios, usa `/diff` para revisar los estilos antes de aprobarlos.
<!-- track:cli:end -->

## Tarea 3: Ajusta el aspecto

> **⚠️ ¿No ves los cambios?** Si no aparecen el tema o las animaciones, detén el servidor de desarrollo (`Ctrl+C`), vuelve a iniciarlo con `npm run dev` y fuerza la recarga (`Ctrl+Shift+R`) en el navegador.

Mantén abierta la vista previa en el navegador e itera sobre el diseño. Prueba prompts como:

> El efecto de líneas de barrido es demasiado intenso; reduce la opacidad a 0.03.

> Añade un sutil parpadeo eléctrico al texto del título.

> La insignia VS debería pulsar de forma más llamativa.

Este es un enfoque de **desarrollo orientado al diseño**: iteras sobre el resultado visual en tiempo real. Cada prompt perfecciona la experiencia hasta que tenga el aspecto adecuado. No te conformes con «suficientemente bien»: sigue ajustando el diseño hasta que la página parezca pertenecer a una máquina recreativa.

## Tarea 4: Actualiza las instrucciones

Las instrucciones deben reflejar las decisiones de diseño importantes para que los prompts posteriores mantengan la coherencia.

<!-- track:vscode:start -->
Pide a Copilot Chat:

> Añade a `copilot-instructions.md` una sección de guía de diseño que describa nuestro tema de arcade retro: colores, fuentes y estilo de animación.
<!-- track:vscode:end -->

<!-- track:cli:start -->
Pide a Copilot CLI:

> Actualiza las instrucciones del repositorio con una guía breve de diseño para el tema de arcade retro: colores, fuentes, estilo de animación y la regla de que las nuevas interfaces mantengan la estética de neón.
<!-- track:cli:end -->

Cuando la página tenga el aspecto adecuado, haz commit de las instrucciones y los cambios de diseño.

## ✅ Parte 4 completada

**Lo que has aprendido:**

- Usar flujos de planificación para diseñar un **sistema visual antes de implementarlo**
- **Iterar sobre el resultado visual** con comentarios de seguimiento rápidos
- **Actualizar las instrucciones después de tomar decisiones importantes** para que Copilot mantenga la identidad visual
