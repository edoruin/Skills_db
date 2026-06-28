# SKILL NAME:  SAVE-CHANGES SKILL
# DESCRIPTION: Evita la regresión de código y la pérdida de cambios previos al aplicar nuevas modificaciones, utilizando un esquema de revisión estructurado y quirúrgico.

## 1. Esquema de Revisión Obligatorio (3-Way State)
Antes de generar o modificar cualquier línea de código, debes identificar y mapear mentalmente tres estados del archivo:
* **[ESTADO_A] Código Base:** El estado original y la arquitectura fundacional del archivo antes de la sesión actual.
* **[ESTADO_B] Cambios Previos Aprobados:** Las modificaciones, refactorizaciones o correcciones recientes introducidas en las interacciones pasadas. Estas son **sagradas** y no deben ser revertidas, omitidas ni simplificadas.
* **[ESTADO_C] Nueva Mutación:** El nuevo requerimiento o cambio a implementar. Su integración debe encapsularse sin contaminar el ESTADO_B.

## 2. Reglas Estrictas de Modificación (Reglas de Intervención)
Para aplicar el [ESTADO_C], debes adherirte estrictamente a lo siguiente:
1.  **Edición Quirúrgica:** No reescribas ni regeneres funciones, clases o archivos completos si solo necesitas modificar una parte. Limítate a alterar exclusivamente las líneas necesarias.
2.  **Principio de No Regresión:** Nunca elimines lógica de manejo de errores, variables de estado, importaciones o validaciones que fueron agregadas recientemente, a menos que el usuario lo solicite explícitamente.
3.  **Preservación de Firmas:** No modifiques las firmas de las funciones (parámetros o retornos) si esto rompe implementaciones previas en otras partes del código.
4.  **Parada de Seguridad (Stop & Ask):** Si la [Nueva Mutación] entra en conflicto directo con los [Cambios Previos Aprobados] o requiere sobrescribirlos para funcionar, **no generes el código**. Detente y explícale el conflicto al usuario para pedir confirmación.

## 3. Protocolo de Respuesta (Output Format)
Antes de emitir cualquier bloque de código, debes generar un breve reporte técnico usando esta estructura exacta:

**[Análisis de Impacto]**
* **Target:** (Nombre de la función/archivo a modificar)
* **Preservación:** (Qué cambio previo estás protegiendo activamente)
* **Riesgo de Colisión:** (Ninguno / Bajo / Alto - requiere confirmación)

**[Código Propuesto]**
(Emite únicamente el bloque de código modificado, incluyendo 2 o 3 líneas de contexto por encima y por debajo del cambio para guiar al cursor, sin regenerar el resto del archivo).

## 4. Checklist de Validación (Self-Correction antes de emitir)
Responde mentalmente a esto antes de mostrar tu respuesta:
- [ ] ¿He mantenido intactas las lógicas y variables agregadas en el prompt anterior?
- [ ] ¿Estoy mostrando solo el fragmento necesario en lugar de todo el archivo?
- [ ] ¿La nueva implementación rompe el funcionamiento del ESTADO_B?

Si alguna respuesta indica pérdida de código previo, reescribe tu solución antes de responder.
