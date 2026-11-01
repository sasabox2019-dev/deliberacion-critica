# CHANGELOG

Todos los cambios notables del PROMPT MAESTRO. Cada versión nace de un fallo observado en deliberaciones reales, no de teoría.

## [2.5] — Arranque conversacional

**Motivado por:** la fricción de rellenar plantilla hacía que la gente pegara el prompt incompleto y el comité deliberara con datos fantasma.

- Arranque conversacional: el prompt se puede pegar vacío y el orquestador entrevista en UN solo mensaje, preguntando solo lo que falte.
- El MODO ya no se pregunta a ciegas: el orquestador lo recomienda según riesgo e irreversibilidad; el usuario lo cambia con una palabra.
- El IDIOMA se deduce del mensaje; solo se pregunta ante ambigüedad real.
- Dos preguntas nuevas de alto valor: pérdida máxima tolerable (alimenta el stop-loss) y fecha límite para decidir.
- Prohibido inventar variables vacías: quedan como [ESTIMACIÓN].

## [2.2] — Protocolo de Enrocamiento

**Motivado por:** el escenario de bloqueo con posturas críticas incompatibles — un livelock de incentivos donde los agentes hacían exactamente lo que se les ordenaba (no ceder) y el debate no convergía.

- **Protocolo de Enrocamiento (regla 5-bis)**: tras una exigencia PARCIAL/RECHAZADA dos veces, el Proponente puede declarar TRADE-OFF IRREDUCTIBLE con motivación → intervención de intereses (posiciones → intereses, estilo Fisher-Ury) → si son compatibles, mecanismo; si hay asimetría, laudo jerárquico del árbitro (CATASTRÓFICO existencial > fricción matadora > ALTO > MEDIO) con sacrificio mínimo cuantificado; si hay simetría real, gate empírico (experimento del mundo real que decide por datos).
- **Muerte del nodo como terminal válido**: un segundo enrocamiento sobre el mismo nodo = RECHAZADO de ese nodo con descope o división del proyecto. La reconciliación cosmética queda prohibida.
- **Parche del alcance del sello [VERIFICADO]** (post-duelo de motores): el sello solo apunta a fuente externa con fecha buscada por el agente que firma; jamás a argumentos internos del debate. Toda cifra sin fuente es [ESTIMACIÓN]. Detectado en producción tres veces.
- **Parche anti-anclaje (Versión A)**: la relectura de los propios mensajes sirve para continuidad, no para reafirmar posición — mata el punto fijo del enrocamiento en ventanas lineales.
- **Enmienda anti-pre-hedging**: el v1 del Proponente es el extremo honesto del objetivo original; retirar opciones antes del ataque les roba el trabajo a los críticos y comprime el debate. Detectado en las dos carreras del duelo.

## [2.1] — División en dos versiones

**Motivado por:** los límites físicos de un chat lineal (colapso de salida, fusión de personalidades, amabilidad de la IA).

- **Versión A (chat)**: ejecución por bloques con «CONTINÚA», cabeceras de rol, regla «los roles nunca coinciden del todo», topes de palabras por intervención, LIGERO por defecto.
- **Versión B (agentes)**: Abogado del Diablo estrictamente destructivo (requisitos verificables, nunca soluciones de diseño), verificación arquitectónica ([VERIFICADO] exige ejecutar la búsqueda en el propio contexto), orquestador sin contenido técnico («el juez no puede jugar»), advertencia del sesgo residual de modelo único con mitigación (modelos distintos por crítico si la plataforma lo permite).

## [2.0] — Universalización

**Motivado por:** dos deliberaciones reales (bar autónomo de Madrid, tienda de pueblo) que destaparon cinco carencias del original.

- Roles generalizados: Ingeniero → **Proponente** (cualquier dominio); Cliente → **Parte Afectada** (quien vive las consecuencias).
- **Criterio de terminación**: veredicto terminal con formato obligatorio (A: exigencia por exigencia; B: ¿queda CATASTRÓFICO?; C: APROBADO/CON CONDICIONES/RECHAZADO).
- **Taxonomía de severidad común** (CATASTRÓFICO/ALTO/MEDIO/BAJO) + mecanismo de fallo obligatorio en cada ataque.
- **Regla de verificación**: [VERIFICADO: fuente] vs [ESTIMACIÓN]; prohibido disfrazar estimaciones de datos.
- **Protocolo de contradicciones** entre críticos («contradicción viva» + mecanismo reconciliador).
- **Entregable plantillado** de 8 secciones, con gates de decisión y frontera profesional.
- **Modos** LIGERO / COMPLETO / PROFUNDO.

## [1.0] — Prompt original

Comité de 4 roles (Ingeniero, Abogado del Diablo, Cliente Escéptico, Experto Especialista), mínimo 3 intervenciones cruzadas por agente, orquestador taquígrafo prohibido de resolver directamente, Maestro compilador al cierre. Estrenado y estresado con el caso del bar autónomo de Madrid.
