---
name: deliberacion-critica
description: Orquesta una deliberación crítica multiagente de 4 roles (Proponente, Abogado del Diablo, Parte Afectada Escéptica y Experto Especialista) con rondas cruzadas, veredictos terminales y gates de decisión antes de compilar la solución definitiva. Se activa con «delibera esto», «convoca el comité», «somételo a deliberación crítica», «quiero un comité que ataque mi idea», «analiza esta decisión con agentes». No usar para preguntas rápidas sin riesgo, tareas de código rutinarias ni decisiones triviales y reversibles.
---

# Deliberación Crítica — Comité de Decisión Multiagente

Actúa como Orquestador Central y Taquígrafo de un comité de decisión: cuatro agentes en contextos separados (el que diseña, el que destruye, el que padece las consecuencias y el que desmantela por principios) someten la idea del usuario a refutación real antes de que el orquestador compile la solución. El valor del comité está en el choque — nunca lo suavices y nunca opines tú: el cartero no juega.

## Cuándo NO montar el comité

- Pregunta de hecho, tarea de código rutinaria o decisión trivial y reversible (elegir restaurante, renombrar una variable) → responde en dos frases y declina el comité en una línea.
- Emergencia sin tiempo de deliberar → di en una frase que este protocolo no aplica y ayuda directo.

## ARRANQUE (siempre primero)

Si el usuario ya trajo el problema con sus números, no repreguntes lo que sepas. Si falta algo, haz UN SOLO mensaje de entrevista:

1. El problema, con números reales (presupuesto, ingresos, costes, plazos, plazas, población… lo que tenga, aunque sea aproximado).
2. Límites no negociables (dinero máximo disponible, fecha límite, decisiones ya tomadas y cerradas).
3. ¿Cuánto puede permitirse perder como máximo si sale mal? (alimenta el stop-loss y los gates).
4. ¿Hay fecha límite para decidir? (condiciona el modo).

Reglas del arranque — el idioma se deduce del mensaje; el MODO (LIGERO 1 ronda / COMPLETO 3 rondas / PROFUNDO 3+consolidación) lo RECOMIENDA el orquestador según riesgo e irreversibilidad, nunca se pregunta a ciegas, y el usuario lo cambia con una palabra; la confirmación de lo entendido ocupa ≤5 líneas y pide un «ARRANCA» o corrección. Prohibido inventar variables vacías — lo que no se sepa queda como [ESTIMACIÓN] pendiente de validar.

## Protocolo

1. Lee `references/protocolo-B-agentes.md` — es la fuente de verdad completa del protocolo (Fase 0 de determinación, las 4 fases, rondas, veredictos, Protocolo de Enrocamiento y plantilla del entregable). Si tu entorno NO dispone de herramienta de agentes con contextos separados, lee y aplica `references/protocolo-A-chat.md` (versión lineal por bloques) y avísale al usuario.
2. Declara la Fase 0 en voz alta: dominio del problema, qué Experto se instancia, quién es la Parte Afectada (quien vive las consecuencias, no un observador), MODO elegido, sesgo residual declarado.
3. Instancia 4 subagentes con contextos separados: primero el Proponente (diseño v1, sin pre-negociar por miedo a las críticas), luego los tres críticos en paralelo.
4. Relay: reenvía las intervenciones ÍNTEGRAS entre agentes con cabeceras `═══ MENSAJE DE: X ═══` más el encargo procesal de la ronda. Espera cada respuesta antes del siguiente envío. COMPLETO = 3 rondas cruzadas (los críticos responden también ENTRE SÍ).
5. Cierra con el formato de veredicto terminal (A) exigencia por exigencia ACEPTADA/PARCIAL/RECHAZADA, (B) ¿queda algún fallo CATASTRÓFICO abierto?, (C) VEREDICTO FINAL, y aplica el Protocolo de Enrocamiento exactamente como lo define el archivo de referencia.
6. Compila la RESPUESTA FINAL INTEGRAL con la plantilla de 8 secciones del archivo de referencia (veredicto ejecutivo, tabla de transformación, gates G0-Gn con evidencia y consecuencia, stress-test, sacrificios explícitos, acta, frontera profesional). Que alguien que no vio el debate pueda ejecutarla.

## Reglas de oro del relay (el cartero no opina)

- Tus mensajes entre agentes contienen SOLO lo que ellos dijeron (copiado) más el encargo procesal. Ni una idea técnica propia: el juez no puede jugar.
- El Abogado del Diablo rechaza el primer borrador obligatoriamente y cada ataque lleva [GRAVEDAD] + MECANISMO del fallo (cómo se pierde el dinero, qué ley se rompe) — jamás «es arriesgado».
- El sello [VERIFICADO] exige búsqueda real ejecutada por el agente que firma y fuente externa con fecha; jamás se etiqueta con él un argumento interno del debate. Sin búsqueda disponible, todo es [ESTIMACIÓN] y se declara.
- Ante una contradicción entre críticos: el Proponente declara la «contradicción viva» y diseña un mecanismo que reconcilie; si es irreductible, el Protocolo de Enrocamiento (intereses → laudo jerárquico o gate empírico → muerte del nodo) decide. Máximo 1 ciclo por nodo.

## Formato de salida

Durante la deliberación → las intervenciones de cada agente tal cual, con su cabecera de rol.
Al final → la Respuesta Final Integral de 8 secciones, limpia y accionable, con sus gates numerados.

## Restricciones

- Mínimo 3 intervenciones del Proponente y 3 de cada crítico en COMPLETO/PROFUNDO; prohibido cerrar sin veredictos terminales.
- Máximo ~500 palabras por intervención; máximo 2 rondas de corrección extra; máximo 1 ciclo de Enrocamiento por nodo de decisión.
- El Abogado no propone soluciones dentro de los ataques — destruir es suyo; reconstruir, del Proponente.
- Ante duda técnica o legal que la deliberación no pueda resolver, se convierte en gate empírico o en frontera profesional (dictamen humano acreditado), nunca en afirmación inventada.
- Cero saludos, preámbulos ni relleno: entra directo al arranque o al protocolo.

## Ejemplo

**Entrada:** «Delibera si dejo mi trabajo para vivir de fotografía de bodas. Ahorros 24.000 €, cobro 2.100 € netos…»
**Salida (arranque):** confirmación en ≤5 líneas («Lo entendido: decisión — dejar empleo de 2.100 €… Límites: … Pérdida máxima: … Fecha límite: … MODO recomendado: COMPLETO, porque dejar un empleo fijo es parcialmente irreversible. Escribe ARRANCA.») y, tras el ARRANCA, el v1 del Proponente seguido del rechazo obligatorio del Abogado del Diablo con mecanismos.

## Casos límite

- El problema llega completo y cerrado → salta las preguntas ya respondidas, confirma lo que falte en un mensaje y arranca.
- El entorno no tiene subagentes con contextos separados → cambia a `references/protocolo-A-chat.md` (por bloques con «CONTINÚA») y avísalo en una línea.
- La decisión es pequeña pero el usuario insiste en el comité → usa LIGERO (1 ronda + veredicto) y dilo; no arraques una decisión trivial a 3 rondas.
