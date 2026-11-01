# RESPUESTA FINAL INTEGRAL
## Bar/cafetería de autoservicio sin personal en el centro de Madrid — Solución definitiva de ingeniería (v3)

> Compilada por el Agente Maestro tras la deliberación crítica de 4 subagentes (Ingeniero, Abogado del Diablo, Cliente Escéptico, Experto Especialista en unattended retail y cumplimiento normativo España/UE). Cada agente intervino 3–4 veces en diálogo cruzado; los 3 críticos emitieron veredicto final «APROBADO CON CONDICIONES» y el Ingeniero integró las 12 condiciones como puertas de salida del diseño.

---

## 1. Veredicto ejecutivo

La idea original **tal como estaba planteada no puede existir**: el grifo de cerveza en autoservicio choca con la normativa madrileña de venta de alcohol (Ley 5/2002 CM + LOPSC + ordenanzas: se exige control responsable en el punto de dispensación), la huella dactilar como condición de acceso viola el RGPD (art. 9 y art. 7.4: el consentimiento no es libre si es la única vía de entrada; precedente AEPD), y el «coste de personal = 0» es una categoría económica inexistente (quedan limpieza con registros APPCC, mantenimiento, reposición, soporte remoto 24/7 y el responsable de establecimiento que exige la licencia).

**Lo que sí puede existir, y con margen, es esto:** una **cafetería/tienda de conveniencia diurna de autoservicio** en 60–80 m² del centro de Madrid, **sin alcohol y sin biometría**, con producto 100 % envasado y sellado, cobro por peso discreto de SKU con peso unitario verificado, hardware comprado (no construido), un «personal invisible» de ~25–40 % del coste de un bar tradicional, y un despliegue gobernado por 12 puertas (gates) que convierten cada riesgo catastrófico identificado en la deliberación en una condición contractual de avance.

**Cambios de negocio que la deliberación impuso:**
| Idea original | Qué la mató | Diseño v3 |
|---|---|---|
| Tirador de cerveza inteligente | Venta de alcohol en autoservicio restringida en la CM; verificación de edad en el punto de dispensación | Sin alcohol por diseño (catálogo firmado en firmware); el tirador solo vuelve tras dictamen legal favorable (Gate 0) |
| Huella dactilar | Art. 9 RGPD + consentimiento no libre (art. 7.4) + precedente AEPD | Cero biometría: tarjeta nominal DESFire EV3 + quiosco de turista en puerta |
| Amazon Go nocturno | Pico de salida masiva + coste CAPEX de visión + ilegalidad del alcohol | Comercio diurno de tránsito; peso discreto, sin IA ambigua |
| Personal = 0 | Limpieza APPCC, mantenimiento, reposición, soporte, responsable de licencia | Personal invisible: OPEX 3.000–4.500 €/mes ≈ 25–40 % de un bar tradicional |
| Cobrar «con IA» | Colusión, tara de vaso, swap, bandas que miden umbrales | Cobro conservador: solo delta discreto de peso de SKUs sellados + conciliación diaria |
| Construir microservicios propios | Sobreingeniería para 60–80 m² | Comprar OEM con APIs abiertas; software propio solo como capa de integración y cobro |

---

## 2. Arquitectura definitiva (v3)

### 2.1 Identidad y acceso
- **Tarjeta nominal MIFARE DESFire EV3** (criptográficamente no clonable), sesión única por tarjeta, bloqueo por duplicado, blacklist. Alta: 2 € retornables de tarjeta + 5 € de primera recarga consumible.
- **Quiosco de emisión en puerta** para turistas y walk-in: pago (contactless) + tarjeta RFID de un solo uso con saldo cargado, sin alta y en <60 s. El quiosco es emisor + recargador (contactless y efectivo) + devolución de saldo.
- **Entrada por badge; salida siempre libre** (RSCIEI: nunca se retiene a nadie). El no-repudio vive en la sesión nominal, no en la puerta.
- **Degradación = bloqueo de la ENTRADA, jamás de la salida.** Si el sistema de cobro no funciona, no entra nadie; quien está dentro sale siempre.

### 2.2 Detección de consumo
- Neveras OEM con APIs abiertas + celdas de carga por balda. **Peso unitario verificado por lote en cada reposición** (el operador itinerante confirma el peso real en su app; el sistema no «supone»).
- Solo **producto envasado y sellado**; nada a granel manipulable por el cliente (APPCC: el cliente es el vector de peligro; alérgenos según Reg. 1169/2011 en la etiqueta original).
- Cafeteras superautomáticas con contador de tazas: un evento por taza.
- **Sin alcohol por diseño:** catálogo firmado criptográficamente cargado en el firmware de las neveras y en el validador de cobro; un SKU fuera de catálogo no se registra ni se cobra. Auditoría mensual de catálogo firmado vs. inventario físico.

### 2.3 Cobro y facturación
- Ledger append-only + **SIF/TPV certificado Verifactu de un tercero desde el día 1** (RD 1007/2023; la certificación del OEM no se hereda). El SIF propio se desarrolla en paralelo y solo conmuta tras su certificación.
- **Cero pre-auth:** cobro contra el saldo prepago de la tarjeta al cruzar la salida (exposición máxima = saldo depositado). Si el dictamen del Gate 1 invalida el saldo interno: cobro directo a tarjeta bancaria en la puerta vía PSP.
- Sensor de paso en la puerta única de salida cierra la sesión; sesión abierta sin cruce detectado → aviso + revisión.
- Carrito en vivo en la app como **feature opcional**, nunca requisito de uso.

### 2.4 Mecanismo de reembolso y antifraude (resolución de la contradicción entre críticos)
1. Reembolso **siempre al medio de origen** (misma tarjeta; si el pago fue bancario, a esa tarjeta). Nunca a cuentas nuevas → mata la fábrica de tarjetas desechables.
2. **Sin umbral publicado.** Los eventos 1 y 2 del mismo día (<5 €) se auto-abonan. El 3.º del mismo día pasa a revisión humana <24 h vía intercom.
3. Tope mensual por tarjeta (15 €); agotado el tope, todo reembolso se revisa.
4. **Detector de patrones en el ledger** (mismo SKU/franja/saldo-tensión sistemático) → marcado y bloqueo temporal.
5. **Conciliación nocturna inventario vs. cobros** (job diario) + revisión semanal post-cruce; tarjeta con sesión no conciliable → bloqueada hasta revisión.
6. Todo reembolso genera **asiento SIF espejo** (factura rectificativa simplificada): el antifraude comercial nunca rompe el antifraude fiscal.

### 2.5 Infraestructura
- **Edge server en local ejecuta entrada/cobro/salida sin nube.** La nube es telemetría y BI, no camino crítico (responde al SPOF del PSP/cloud).
- Arquitectura como **contrato de eventos estandarizado** entre componentes comprados (neveras, quiosco, TPV, controlador de puerta), no microservicios propios.
- **Dual-PSP:** principal + segundo contrato latente activable en <48 h, rolling reserve y cuenta técnica con 30 días de colchón para chargebacks.
- Cláusulas OEM obligatorias: exportación diaria de datos, API abierta garantizada, escrow de firmware.
- Continuidad: puerta de salida antipánico mecánica siempre libre, 4G de respaldo, alertas de temperatura (cadena de frío) con respuesta por SLA.

### 2.6 Operaciones invisibles («el personal que ya no se ve»)
- Limpieza diaria contratada con registros APPCC.
- Operador itinerante on-call activado por métricas (niveles de stock, ocupación, alarmas), con ventana nocturna de reposición.
- **Botón físico AYUDA + intercomunicador con SLA humano <2 min, medido y publicado en la puerta.**
- Mantenimiento predictivo + kit de swap de repuestos críticos en local.
- Precios a la vista en el escaparate. Efectivo con reciclador de monedas **contratado para <90 días** tras la apertura.

### 2.7 Privacidad
- Cero biometría en el local. Cámaras solo tras **DPIA aprobado por DPO externo**: enmascarado, sin reconocimiento facial, sin identidad en frames, retención ≤72 h, cobertura solo para excepciones (no permanente). Registro de actividades (art. 30 RGPD); consulta previa (art. 36) si la analítica resultara sistemática a gran escala.

---

## 3. Flujo del cliente end-to-end
1. **Socio:** recarga en quiosco o app → badge en la entrada → sesion abre. **Turista:** quiosco (pago + tarjeta de un solo uso) → badge → entra en <60 s sin alta.
2. Abre la nevera, toma lo que quiera (baldas con peso), pide café (contador de tazas).
3. Cruza la salida: el sensor cierra la sesión, el sistema descuenta el saldo y emite ticket conforme Verifactu (recibo en pantalla + email si hay alta).
4. ¿Error? Primer/segundo evento <5 € del día → auto-abono al medio de origen en <60 s. Tercero o tope agotado → intercom + revisión humana <24 h.
5. Cierre nocturno: job de conciliación inventario-cobros; anomalías → bloqueo de tarjeta + cola de revisión; niveles de stock → tarea de reposición para el itinerante.

---

## 4. Puertas de despliegue (G0–G11): el proyecto no avanza si no las cruza
| Gate | Condición | Consecuencia si falla |
|---|---|---|
| **G0** | Dictamen legal firmado (autoservicio envasado sin alcohol + cita normativa correcta) **antes de gastar un euro de CAPEX** | Proyecto muere, sin excepciones |
| **G1** | Dictamen sobre el saldo prepago (medio limitado a la red del comerciante / e-money, Ley 16/2009–PSD2) | Plan B ya diseñado: cobro directo a tarjeta en puerta |
| **G2** | Póliza RC con «operación sin personal» declarada expresamente a la aseguradora (previa a la firma de la renta) | Sin póliza válida no se firma renta |
| **G3** | SIF certificado de terceros como camino crítico el día 1 | No se abre |
| **G4** | Stress-test a 80 tickets/día publicado antes del CAPEX | Ver §5: obliga a CAPEX modular |
| **G5** | Piloto 90 días con go/no-go contractual; **cláusula de muerte por escrito: shrinkage >2 % de ventas sostenido 30 días** | Cierre o rediseño |
| **G6** | Conciliación semanal + bloqueo automático demostrados en piloto (cierra el hueco del cruce único) | No se pasa a producción |
| **G7** | Reembolso solo al medio de origen + revisión humana sobre umbral | Requisito del mecanismo §2.4 |
| **G8** | **Test del turista ejecutado y cronometrado con personas reales** (<60 s, sin ayuda) como gate de apertura | Sin test superado, no hay apertura |
| **G9** | Saldo de un solo uso gastable hasta 0 € o reembolsable íntegro en quiosco | Ningún céntimo muerto |
| **G10** | Recarga física en quiosco (contactless + efectivo) | La app nunca es requisito |
| **G11** | Segundo evento diario <5 € también auto-abonado (con el guard del §2.4) | Equilibrio fricción/fraude |

---

## 5. Modelo económico (centro de Madrid, 60–80 m²)
- **CAPEX:** 50–70 k€ a escala completa (6–8 neveras OEM, 2 cafeteras superautomáticas, quiosco, DESFire + puertas, edge server, obras). **Despliegue inicial modular: 3–4 neveras**; el equipo se expande comprando, no comprometiendo.
- **OPEX:** 3.000–4.500 €/mes (limpieza 900, itinerante on-call 600, mantenimiento 300, seguros con recargo ~200, SaaS/DPO ~200, renta 1.500–2.500, PSP ~1,5 %).
- **Caso base (200 tickets/día × 4,50 €):** ~27.000 €/mes facturados, margen bruto ~65 % (~17.500 €), beneficio operativo ~11–13 k€/mes, payback <6 meses.
- **Stress test (80 tickets/día, exigido por el Experto):** ~10.800 €/mes, beneficio 500–2.000 €/mes, payback >3 años → por eso el CAPEX es modular y el KPI del piloto es **tráfico**, no tecnología.
- **Riesgo dominante del negocio: comercial (captar 200 uds/día), no técnico ni legal** (una vez cruzado G0).

---

## 6. Plan de despliegue
1. **Fase 0 — Gobernanza (semanas 1–6):** dictamen legal (G0) + dictamen e-money (G1) + póliza declarada (G2) + stress-test publicado (G4). Coste: consultoría. CAPEX: 0 €.
2. **Fase 1 — Piloto (semanas 6–18):** instalación modular (3–4 neveras, 2 cafeteras, quiosco, edge, SIF tercero), test del turista cronometrado (G8), piloto 90 días con KPIs contractuales (onboarding <30 s, % sesiones con revisión, shrinkage, ticket medio) y go/no-go (G5–G6).
3. **Fase 2 — Escala del local (post-piloto):** hasta 8 neveras, reciclador de efectivo, SIF propio certificado. Alcohol/tirador **solo si** un dictamen específico lo hace viable.
4. **Fase 3 — Réplica:** segundo y tercer local con el mismo stack y las mismas puertas.

---

## 7. Riesgos residuales (conocidos y acotados)
- Robo en cruce único: acotado por saldo prepago, conciliación diaria y bloqueo automático (G6).
- Dependencia del OEM/SaaS: cláusulas de escrow, exportación diaria, API garantizada.
- Fraude organizado: umbrales no publicados, topes por tarjeta, detector de patrones, conciliación.
- Inspecciones (laboral, tributaria, consistorial): diseño para inspección — licencia coherente, responsable nominado, logs auditables, SIF conforme.
- Seguro: operación declarada expresamente (G2), siniestralidad documentada por telemetría.
- Público nocturno perdido: decisión explícita de negocio (no competir en un campo ilegal).

---

## Anexo — Acta de la deliberación
| Agente | Intervenciones | Aporte clave | Veredicto final |
|---|---|---|---|
| Ingeniero | 4 | Diseño v1 → defensa/corrección → v2 integrador → cierre con gates G0–G11 | — (diseñador) |
| Abogado del Diablo | 3 | 10 ataques (alcohol ilegal, RGPD, Verifactu, fraude, continuidad); detectó el sesgo nocturno y el riesgo e-money | Aprobado con condiciones |
| Cliente Escéptico | 3 | Journey del peor caso; test del turista, cero pre-auth, botón AYUDA, efectivo con fecha, precios visibles | Aprobado con condiciones |
| Experto (unattended retail + cumplimiento España/UE) | 3 | First principles (Ley 5/2002 CM, art. 7.4 RGPD, APPCC, Verifactu RD 1007/2023), second-order (seguros, bandas, PSP, stress-test) | Aprobado con condiciones |

Fallos catastróficos encontrados y resueltos: alcohol en autoservicio (eliminado por diseño), biometría (eliminada), "no cobrar si duda" (sustituido por cobro conservador + conciliación), entrada libre en degradación (sustituida por cierre de entrada), recibo no conforme (SIF Verifactu día 1), saldo prepago sin calificar (Gate 1 con plan B), póliza no declarada (Gate 2).
