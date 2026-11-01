# RESPUESTA FINAL INTEGRAL
## Mini-supermercado / tienda de alimentación en Yécora (Álava) — Solución definitiva (v3)

> Compilada por el Agente Maestro tras la deliberación crítica de 4 subagentes (Ingeniero, Abogado del Diablo, Vecino Escéptico, Experto Especialista en retail de proximidad y comercio rural). Cada agente intervino 3–4 veces en diálogo cruzado con datos verificados por búsqueda web. Veredictos finales: Vecino **APROBADO PARA PRODUCCIÓN** (1 nota), Abogado **APROBADO CON CONDICIONES** (4), Experto **APROBADO CON CONDICIONES** (5). Las 10 condiciones quedaron integradas como puertas G0–G4.

---

## 1. Veredicto ejecutivo

La idea original —mini-súper tradicional **con dependiente**, abierto de 6:30 a 00:00— **no cierra como está planteada**, y no por falta de esfuerzo sino por aritmética y por historia:

1. **Yécora tiene ~270 habitantes (265 INE 2024 / 274 Eustat 2025), unos 110–120 hogares.** El gasto diario incremental de todo el pueblo ronda los 150–250 €/día. Con ticket real de conveniencia de 2,5–3 €, la demanda plausible es de **25–40 tickets/día**, no los 80 × 5 € del primer borrador.
2. **Un súper con empleo asalariado no cierra en Yécora**: con una sola nómina externa (coste real ~1.400–1.500 €/mes) el punto de equilibrio exige ~140 tickets/día, inalcanzable. Dos nóminas (2.600–3.000 €/mes) lo hacen imposible.
3. **La "oportunidad" ya fue probada y fracasó**: Yécora figura entre los siete municipios de Álava que se quedaron **sin ningún comercio** tras perderse ~200 negocios entre 2019–2022 (El Correo, 2023). Que el pueblo sobreviva sin tienda demuestra que la demanda esencial está **reubicada** (coche hasta Laguardia ~15 km / Logroño ~34 km, panadero que reparte a domicilio desde hace 30 años, el bar del pueblo, abierto), no sin servir.
4. Los horarios extremos también caen: a las 6:30 solo compran café los de la bodega y la guardia civil del puesto cercano (~8 clientes); y el pan del día como gancho vale cero porque el panadero ya lo deja en el portal a las 8:00.

**Lo que sí puede existir — y con riesgo total acotado — es esto:** un **piloto de medición de 6 meses con exposición total ≤9.000 €** (CAPEX <6.000 € + stop-loss de 3.000 €), sin nóminas, operado por la familia como **complemento de renta aceptado por escrito**, en un local mínimo, con oferta recortada a 150 referencias, horario realista, alianzas con el panadero y el bar en lugar de competencia contra ellos, y **tres salidas escritas**: cierre barato, modo estabilizado (retirada de 400–800 €/mes desde el mes 7 solo si el flujo la cubre) o convocatoria de escala (jamás "contratar y ver").

**La frase que resume el debate:** *esta tienda no se abre para vivir de ella; se abre para saber con números si puede existir — y el día que los números digan que no, la mejor arquitectura es la que ya previó la salida.*

---

## 2. Lo que cambió respecto a la idea original

| Idea original | Qué la mató | Diseño v3 |
|---|---|---|
| Mini-súper con dependiente (nómina) | BE de ~140 tickets/día con 1 sueldo; demanda real 25–40 tickets/día | Negocio familiar sin nóminas (autoempleo aceptado por escrito); nómina solo tras nueva deliberación con exposición ≤15.000 € |
| Abrir 6:30 | Solo 8 clientes a esa hora; el pan ya llega a domicilio a las 8:00 | 8:00–13:30 / 17:00–20:30 + domingo mañana |
| Cerrar a las 00:00 | No hay demanda probada; quemazón familiar | Noche (20:30–22:30) solo viernes y sábado, con campanilla, y SOLO si sostiene ≥15 tickets/noche en 4 semanas consecutivas |
| Pan del día como gancho | El panadero entrega en el portal desde hace 30 años | **Punto de recogida del panadero**: no competirle, convertirla amenaza en canal (tráfico a cambio) |
| Café de máquina desde las 6:30 | Canibalizaría al bar del pueblo ("el bar es del pueblo y la tienda no") | Café a las 8:00, peso CERO en ingresos; pacto con el bar cerrado de boca del dueño |
| Sándwiches/tortilla de nevera (envasado propio) | Registro sanitario de operador alimentario + merma estructural 8–15% + la tortilla de una vecina | Solo producto ya envasado por el proveedor; pizzas congeladas crudas a precio del Cash; la tortilla de terceros se encarga, no se compite |
| 600–800 referencias | Un súper de urbanización para 120 hogares | **150 referencias bien elegidas**; sin rotación demostrada no entra producto nuevo |
| Fiados de toda la vida | "Ya vi a un vecino de un pueblo cercano perder 3.000 € en fiados" | Libreta con tope: 100 €/familia, techo agregado 1.000 € (subible a 1.500 € si a los 3 meses la mora es cero), conciliación mensual |
| Negocio familiar "viable" por definición | Autoempleo disfrazado (sueldo hora 2–8 €) | Sueldo hora real publicado cada mes + hoja firmada con expectativas + coste de oportunidad declarado (2.600–3.000 €/mes) |

---

## 3. El diseño definitivo (v3)

### Fase 0 — Piloto de medición (meses 1–6)
- **Local mínimo:** ≤40 m², renta ≤150 €/mes, sin obra, contrato con cláusula de salida a los 3 meses.
- **CAPEX <6.000 €:** frigorífico + arco congelador, estanterías, campanilla, datafono, rótulo. Colchón de 3.000 € que incluye fondo de avería del frío (450 €).
- **Exposición total ≤9.000 €** (CAPEX + stop-loss). **Stop-loss automático:** cierre si la pérdida acumulada llega a 3.000 € o a los 6 meses, lo primero, sin veto familiar.
- **Oferta:** 150 referencias (seca básica 20–22% margen, frío envasado ≥28%, congelados listos para horno/air fryer ~30%, chucherías, bebidas). Sin envasado propio. Pan de tercero solo como punto de recogida (RD 308/2019: identificación del elaborador y trazabilidad).
- **Horario:** L–S 8:00–13:30 y 17:00–20:30; domingo 8:00–13:30. Franja nocturna v–s 20:30–22:30 con campanilla como hipótesis a medir (≥15 tickets/noche en 4 semanas consecutivas o fuera).
- **Métricas (escritas, semanales):** tickets/día, ticket medio, margen bruto y merma por módulo (merma ≤5%), cesta nocturna, registro de horas → sueldo hora real publicado. **Septiembre (vendimia) siempre excluido** de toda métrica de decisión.
- **Crédito vecinal:** 100 €/familia, techo agregado 1.000 €, cierre y conciliación mensual. Sin excepciones.
- **No canibalizar al bar:** nada de cervezas, bocadillos ni café-salón que el bar del pueblo ya sirva; solo lo que el bar no tiene.

### Mes 6 — Decisión única y escrita (G3)
Tres salidas, ninguna por inercia: **(a) cierre barato** con plan B de liquidación de activos; **(b) modo estabilizado** — retirada de 400–800 €/mes entre ambos desde el mes 7 solo si el flujo de caja la cubre sin tocar el colchón, tope de 45 h/semana/persona, revisión trimestral con stop-loss vivo; **(c) convocatoria de escala** solo si se supera el gate (≥40 tickets/día sostenidos 3 meses + margen ponderado ≥25%, frío ≥28% / seca ≥22%). **Condición del valle:** sin datos de noviembre–enero, la decisión se aplaza al mes 9. La merma medida y el margen real por módulo son inputs obligatorios de la decisión. Sin firma, se cierra.

### Sistemas mínimos (lo que el vecino pidió)
Datafono + libreta de fiados con tope; encargos por llamada o de palabra en la calle; inventario simple (hoja o app gratuita) solo para merma y rotación; sin TPV cloud de pago mensual ni apps.

---

## 4. Puertas G0–G4 (nada avanza sin cruzarlas)

| Gate | Condición |
|---|---|
| **G0 — Pre-CAPEX** (todo documental, antes de un euro) | ≥25 hogares con pedido anticipado y **señal económica real** (no encuesta de cortesía); carta escrita del Ayto. de Yécora sobre café en vaso (actividad mixta comercio/hostelería), alcohol y horarios; precios y mínimos de pedido firmados de mayorista, panadero y Cash; seguro RC contratado; pacto con el bar del pueblo **cerrado de boca del dueño**; hoja familiar firmada incluyendo la cuota de autónomo (tarifa plana ~80 €/mes) en los fijos |
| **G1 — Estructura** | Local ≤40 m², renta ≤150 €/mes, salida a 3 meses; fondo de avería del frío (450 €) dentro del colchón; exposición total ≤9.000 €; stop-loss vivo |
| **G2 — Operación** | Registro semanal de margen y merma por módulo (merma ≤5%); sueldo hora real publicado; relevo pactado por escrito para bajas ≤5 días (vecino o bar); crédito con tope y conciliación |
| **G3 — Mes 6** | Decisión única escrita: cierre / estabilizado / convocatoria de escala; requiere datos de valle invernal (si no, aplaza a mes 9) |
| **G4 — Escala** (solo si G3 la convoca) | Nueva deliberación con límites duros: exposición total ≤15.000 €, UNA nómina externa única, cobertura de ausencias contratada. Jamás "contratar y ver" |

---

## 5. Números finales (corregidos; estimaciones a validar con los precios firmados del G0)

- **Inversión y riesgo total:** ≤9.000 €.
- **P&L del piloto:** ventas 2.200–3.500 €/mes (25–40 tickets/día × ~2,75 €); margen bruto ponderado 20–25% → 450–850 €/mes; fijos 430–850 €/mes (renta ≤150, frío, seguro, **cuota de autónomo ~80 €**); **resultado: −400 a +420 €/mes**. El Abogado corrigió el rango optimista original: la cuota de autónomo volteaba el rango −100/+300. Se asume como **coste de comprar información**.
- **Modo estabilizado (desde el mes 7):** retirada objetivo 400–800 €/mes entre ambos, solo si el flujo la cubre; techo natural de mercado (~270 hab.).
- **Escala:** solo con exposición ≤15.000 € y una nómina, y solo tras nueva deliberación.

---

## 6. Cumplimiento (resuelto documentalmente en G0, no "a después")
- Licencia/declaración responsable municipal (Ayto. de Yécora) + consulta escrita sobre actividad mixta (café en vaso) y alcohol.
- Horarios: libertad para comercio <300 m² en CAV (Ley 1/2004 + Decreto 33/2005) con comunicación previa — verificar ordenanza local igualmente.
- Pan de tercero: RD 308/2019 (identificación del elaborador, trazabilidad). Sin obrador propio.
- Notificación sanitaria, APPCC básica y carné de manipulador; cadena de frío; alérgenos Reg. UE 1169/2011 (solo envasado del proveedor → sin registro de operador alimentario propio).
- Seguro de RC y contenido antes de abrir.

---

## 7. Riesgos residuales (declarados y vivos)
- **Dependencia del panadero:** su aceptación no está garantizada a 24 meses y su jubilación rompe el canal de tráfico (mitigación: acuerdo firmado en G0 + precocidos como plan B).
- **Coste social de la mora:** cobrar en un pueblo de 265 habitantes (mitigación: tope + conciliación mensual + "el dato manda a los 3 meses").
- **Valle invernal y estacionalidad:** vendimia excluida de métricas; decisión de mes 6 exige datos de valle (o mes 9).
- **Avería del frío:** fondo de 450 € en el colchón o seguro de equipos.
- **Canibalización inversa:** que el bar añada básicos (mitigación: pacto personal con el dueño — nota del vecino: de boca, no de papel).
- **Cobertura de ausencias:** relevo escrito para bajas ≤5 días; sin relevo, el piloto publica su horario real, nunca promesas incumplibles.

---

## Anexo — Acta de la deliberación
| Agente | Interv. | Aporte clave | Veredicto final |
|---|---|---|---|
| Ingeniero | 4 | v1 con datos verificados (Yécora 265–274 hab., Laguardia 15 km, Logroño 34 km) → recálculo honesto ("un súper con nóminas no cierra") → piloto de medición → integración de 10 condiciones como G0–G4 con corrección contable | — (diseñador) |
| Abogado del Diablo | 3 | Demanda imaginaria (400 €/mes por hogar irreal), "¿por qué nadie abrió ya?" (7 municipios de Álava sin comercio), suministro sin compromisos, actividad mixta, cuota de autónomo ausente en los fijos | Aprobado con condiciones (4) |
| Vecino Escéptico | 3 | Panadero a domicilio 30 años, compra grande en Logroño, café de 6:30 = 8 clientes, tortilla de una vecina, 150 referencias, libreta con tope, horario real, "si esperan vivir de esto, que no abran" | Aprobado para producción (nota: pacto con el bar de boca del dueño) |
| Experto (retail de proximidad rural) | 3 | First principles (demanda reubicada, drop sizes, margen real 10–15%, autoempleo), second-order (vendimia, valle, mora, panadero), stop-loss, precompromiso con señal, sueldo hora real | Aprobado con condiciones (5) |

Fallos catastróficos encontrados y resueltos: demanda sobredimensionada 3–4× (escenarios 25/40 tickets), nómina imposible (cortafuegos salarial), horario 6:30–00:00 (recortado y franja nocturna condicionada), pan y café como ganchos falsos (alianzas: punto de recogida + pacto con el bar), envasado propio (eliminado), fiados sin tope (100 €/familia, techo 1.000 €), P&L sin autónomos (corregido a −400/+420 €/mes), estacionalidad (vendimia excluida; valle exigido), escala por inercia (decisiones escritas con exposición máxima).
