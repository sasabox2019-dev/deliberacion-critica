# 🏛️ Deliberación Crítica Multiagente

**El prompt maestro que convierte cualquier decisión importante en un comité de cuatro agentes que diseñan, destruyen, padecen y desmantelan tu idea — antes de que gastes un euro.**

Funciona como prompt copiable (dos versiones) o como skill instalable. Probado en tres deliberaciones reales completas, dos plataformas y un duelo de motores cruzado.

---

## El problema que resuelve

Cuando le pides a una IA que analice una idea, te la **aprueba**. Los modelos tienden a la convergencia prematura: la primera idea contamina todo lo demás y la complacencia hace el resto. Este sistema fuerza lo contrario — una **sala de deliberación** donde tu idea tiene que sobrevivir a un ataque organizado antes de convertirse en plan.

```
                    ┌──────────────────┐
                    │  TU PROBLEMA     │
                    └────────┬─────────┘
                             ▼
        ┌────────────────────────────────────────┐
        │  FASE 0 · Determinación                │
        │  dominio → experto → parte afectada    │
        └────────────────┬───────────────────────┘
                         ▼
   PROONENTE ──diseño v1──► ABOGADO DEL DIABLO ─┐
        ▲            (rechazo obligatorio)       │  3 rondas
        │                                        │  cruzadas
   PARTE AFECTADA ESCÉPTICA ◄──── EXPERTO ──────┘
                         ▼
        ┌────────────────────────────────────────┐
        │  VEREDICTOS (A/B/C) · Protocolo de     │
        │  Enrocamiento si hay trade-offs duros  │
        └────────────────┬───────────────────────┘
                         ▼
   RESPUESTA FINAL INTEGRAL + GATES (G0…Gn)
   «no gastes un euro hasta verificar X»
```

## Los cuatro roles

| Rol | Trabajo | Regla dura |
|---|---|---|
| **Proponente** | Diseña la solución y la defiende | Cede solo ante mecanismos de fallo demostrados; su v1 es el extremo honesto del objetivo original (sin pre-recortes) |
| **Abogado del Diablo** | Destruye con rigor | Rechazo obligatorio del primer borrador; cada ataque lleva gravedad + **mecanismo** (cómo se pierde el dinero, qué ley se rompe). Jamás propone soluciones |
| **Parte Afectada Escéptica** | Es quien vive las consecuencias | Recorre el peor caso posible y declara qué fricción la mata («si no cambias esto, no entro») |
| **Experto Especialista** | Se determina según el problema | Desmantela por first principles y prevé efectos de segundo orden, citando fuentes o marcando «a verificar» |

El orquestador solo reenvía mensajes (el cartero no opina) y compila al final.

## Las dos versiones

| | **Versión A — chat lineal** | **Versión B — agentes** |
|---|---|---|
| Dónde | ChatGPT, Gemini, Claude, DeepSeek (web/app, sin agentes) | ZCode, Claude Code, Chatbox Work Mode, entornos agénticos |
| Cómo corre | Un cerebro interpreta 4 roles, por bloques con «CONTINÚA» | 4 subagentes con memoria propia; el orquestador reenvía |
| Verificación | Declarativa (sin búsqueda → todo [ESTIMACIÓN]) | Arquitectónica (el subagente ejecuta la búsqueda en su contexto) |
| Úsala para | Refinar ideas rápido, móvil, decisiones menores | Riesgo real: dinero, contratos, decisiones difíciles de deshacer |

👉 **[prompts/version-A-chat.md](prompts/version-A-chat.md)** · **[prompts/version-B-agentes.md](prompts/version-B-agentes.md)** — cópialos, rellena 4 variables (o pégalo vacío: v2.5 te entrevista), y arranca.

## El arranque v2.5 (entrevista en un mensaje)

Pega el prompt vacío y el sistema te pregunta **solo lo que falte, todo junto**: el problema con sus números, los límites no negociables, cuánto puedes permitirte perder si sale mal y si hay fecha límite. El modo (LIGERO / COMPLETO / PROFUNDO) **no se te pregunta: se te recomienda** según el riesgo. Confirmación en 5 líneas, escribes «ARRANCA», y empieza el debate.

## El entregable

Toda deliberación termina en un documento ejecutable de 8 secciones, del que la más valiosa son los **gates de decisión**:

> **G0 — Verificación primaria**: dictamen legal firmado antes de un euro de CAPEX; régimen adverso → muerte del proyecto. **G4 — GO/NO-GO**: ≥38 reservas pagadas → gasto; banda roja → apertura solo con tesorería garantizada y disparador de salida.

Cada riesgo catastrófico encontrado en el debate se convierte en una puerta verificable con evidencia y consecuencia. Nada relevante se gasta o se firma sin cruzar su gate.

## Casos de estudio (deliberaciones reales, completas)

| Caso | Veredicto | Lección |
|---|---|---|
| [Bar autónomo de Madrid](casos/01-bar-autoservicio-madrid.md) | El concepto nocturno era ilegal (alcohol en autoservicio) y la biometría, inviable (RGPD) → renace como cafetería diurna con 12 gates | El comité mata la idea central si hace falta y el negocio sobrevive transformado |
| [Tienda de Yécora (270 hab.)](casos/02-tienda-yecora.md) | «Un súper con nóminas no cierra aquí» → piloto de medición ≤9.000 € con stop-loss y salidas escritas | La honestidad numérica vale más que la optimista; piloto que sabe morir |
| [Guardería con cámaras + duelo de motores](casos/03-guarderia-duelo-motores.md) | El directo para padres muere por mecanismo (art. 22 LOPDGDD); el proyecto sobrevive; A y B convergen en terminal por caminos distintos | Validación cruzada de la arquitectura en chat lineal y agentes |

## Instalar la skill

La carpeta [`skill/deliberacion-critica/`](skill/deliberacion-critica/) es una skill portable (formato agentskills.io — compatible con Claude Code, ZCode y Chatbox). Cópiala a tu directorio de skills:

```bash
# Claude Code / ZCode / Chatbox (ruta estándar multi-herramienta)
cp -R skill/deliberacion-critica ~/.agents/skills/

# o, si prefieres prioridad en ZCode
cp -R skill/deliberacion-critica ~/.zcode/skills/
```

Se activa con «delibera esto», «convoca el comité», «somételo a deliberación crítica»… y contiene el protocolo completo dentro de `references/`. Reinicia la app tras copiarla.

## Principios aprendidos en campo

- **Mecanismo, no adjetivos**: una crítica vale solo si explica cómo se pierde el dinero o qué ley se rompe.
- **[VERIFICADO] vs [ESTIMACIÓN]**: el sello exige búsqueda real y fuente externa fechada; jamás valida un argumento interno del debate. La fuente inventada es peor que la estimación declarada.
- **El cartero no opina**: el orquestador reenvía, no delibera. El juez no puede jugar.
- **V1 sin pre-recortes**: el diseñador defiende el extremo honesto de la idea; recortar es trabajo de los críticos.
- **Los trade-offs irreductibles tienen salida**: posturas → intereses → mecanismo, laudo jerárquico o gate empírico; y si un nodo es estructuralmente incompatible, se amputa con descope en vez de fingir reconciliación.
- **Una señal es ruido, dos son patrón**: los parches salen de fallos repetidos en carreras reales; las sospechas sin confirmar se archivan sin tocar nada.

## ⚠️ Límites honestos

- Los casos son deliberaciones ilustrativas sobre promotores ficticios; los datos normativos, demográficos y económicos citados son reales y verificados en su momento, pero **caducan** — re-verifica antes de decidir.
- Este sistema **estructura decisiones y prepara las preguntas**; no sustituye a profesionales acreditados: dictámenes legales, consejo médico, auditorías y contratos requieren humanos con licencia para firmarlos.
- Cada deliberación completa consume tokens significativos: usa LIGERO para lo pequeño y guarda COMPLETO/PROFUNDO para lo que de verdad importa.

## Historial

El sistema evolucionó por fallos de campo, no por teoría: [CHANGELOG.md](CHANGELOG.md) documenta qué se rompió y qué se parcheó en cada versión. Licencia MIT — úsalo, remézclalo y mejora el comité.
