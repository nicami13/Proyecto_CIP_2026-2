# Decisiones del informe — Segundo corte

Registro de las decisiones técnicas y de redacción para actualizar el informe al **segundo corte**.
**Todo lo que se escriba en el documento debe coincidir con este archivo.** Si algo no coincide, no se corrige por cuenta propia: se avisa a Karen García para consultarlo con el equipo.

- Se trabaja directamente en la rama `main`. Solo Karen García y su compañera redactan el documento en este corte; el resto del equipo envía la información y no edita el informe sin avisar.
- Última actualización: 15 de octubre de 2026.
- **Fecha de entrega del segundo corte: 16 de octubre de 2026.**

---

## 0. Ya aplicado en el documento

- **Título:** "Diseño e implementación de un sistema portátil de limpieza CIP". Portada: "Informe técnico de avance — Proyecto Integrador, Segundo corte". Encabezado de página: "Segundo corte".
- **Sección 1:** objetivo general "diseñar e implementar un prototipo funcional…", 5 objetivos específicos, pregunta de diseño, alcance por cortes (1, 2 y 3) y limitaciones actualizadas.
- **Control (indicaciones de Fabián):** potencia de 2000 W en toda la parte de control; se quitaron las dos temperaturas (40/50 °C) y el termostato de seguridad; el PT100 va conectado al PLC, que hace `NORM_X`/`SCALE_X` (sin módulo SM 1231). El controlador de temperatura **aún no está terminado**.
- **Ensayo del modelo:** sí se realizó (datos en `PRUEBAFINAL1.csv`, de Fabián).
- **Sección 2:** texto con paso único a TK-103, tres bombas (P-101, P-102, P-103), transiciones por nivel/temperatura/temporizadores; tabla de fases (20–23 L, 35 °C, tiempo "por medir", destino TK-103); tabla de clasificación actualizada.
- **Tolerancia de temperatura: ±1,75 °C** (5 % de la consigna de 35 °C). REQ-13 debe decir lo mismo.
- **Umbral de seguridad de temperatura: "por definir"** (corte del calentador por programa del PLC; sin termostato).

---

## 1. Cómo trabajamos

1. Antes de empezar: `git pull` (siempre).
2. Cada persona trabaja en **archivos distintos**. Si hay que tocar uno ajeno, se avisa antes.
3. Al terminar: compilar sin errores, y luego `git add` **solo** de `secciones/`, `tablas/`, `figuras/`, `flujogramas/`, `referencias/`, `preambulo/` o `main.tex`, `git commit -m "Sección X: qué se cambió"` y `git push`. Hacer commits pequeños y seguidos para evitar conflictos.
4. **No subir** `main.pdf`, `.aux`, `.log`, `.bbl` ni otros archivos generados al compilar.
5. Tablas, figuras y secciones se citan con `\ref{...}`. **Nunca** se escribe el número a mano.
6. Lo que falte por escribir se marca con `\campo{Pendiente: ...}` (sale en azul en el PDF).

---

## 2. Estructura del documento

| # | Sección | Archivo | Qué hay que hacer |
|---|---|---|---|
| 1 | Contextualización y problema | `02_problema_objetivos.tex` | Ajustar al corte 2 |
| 2 | Caracterización del proceso CIP | `03_caracterizacion_cip.tex` | Ajustar (paso único, 35 °C, volúmenes) |
| 3 | Ingeniería de requisitos | `04_ingenieria_requisitos.tex` | Ajustar requisitos; las Pugh se quedan como referencia |
| 4 | Diseño conceptual mecatrónico | `05_diseno_conceptual.tex` | Ajustar (glosario, P&ID nuevo, sin recirculación) |
| 5 | Diseño de control | `06_control_preliminar.tex` | Ajustar (2000 W, 35 °C, masa) |
| 6 | Comunicaciones industriales | `07_comunicaciones.tex` | Ajustar (Raspberry, S7, AWS, Streamlit) |
| 7 | Plan de validación | `08_plan_validacion.tex` | Ajustar (consignas, REQ-01) |
| 8 | **Montaje físico** (nueva) | `09_montaje_fisico.tex` | Redactar |
| 8.1 | Cambios entre el diseño conceptual y el prototipo | | Tabla: qué cambió y por qué |
| 8.2 | Instrumentación electrónica | | Sensores, actuadores, SSR, alimentación, protecciones |
| 8.3 | Programación | | GRAFCET, mapa de E/S, Ladder v1 |
| 8.4 | Comunicación | | Node-RED, API, Streamlit, evidencias |
| 8.5 | Control | `09_5_validacion_modelo.tex` | Texto de Fabián (validación del modelo) |
| 8.6 | Pruebas | | Resultados y trazabilidad requisito–prueba–resultado |
| 8.7 | Evidencia en video | | Enlace a un video de ~5 min |
| 9 | Gestión del proyecto | `10_gestion_entregables.tex` | Presupuesto real, riesgos, cronograma, checklist |
| 10–11 | Conclusiones y trabajo previsto | `11_conclusiones.tex` | Reescribir (corte 2 y tercer corte) |
| — | Anexos | `12_declaraciones_anexos.tex` | Ajustar |

Indicación de la profesora (Dra. Edna Moriones): sección nueva de montaje físico con instrumentación electrónica, programación, comunicación, control y pruebas; enlace a videos (ideal uno de ~5 min); y **todo lo actualizado debe quedar ajustado en las secciones de planeación**.

Orden de trabajo: (1) ajustar secciones 1–7 → (2) redactar sección 8 → (3) gestión, conclusiones y anexos → (4) revisión completa.

---

## 3. Glosario oficial (usar SOLO estos nombres)

| Tag | Nombre en el documento | Ya no se usa | Programa v1 |
|---|---|---|---|
| — | **Preenjuague** (fase 1) | prelavado, ciclo I | `CICLO = 0` |
| — | **Lavado con detergente** (fase 2) | lavado químico y mecánico, ciclo II | `CICLO = 1` |
| — | **Enjuague final** (fase 3) | ciclo III | (no está en v1) |
| TK-101 | **Tanque de detergente** | tanque de jabón, tanque rojo | — |
| P-101 | **Bomba dosificadora peristáltica** | bomba de jabón | `DOSI` |
| TK-102 | **Tanque de mezcla** | cabina de operaciones, tanque principal, tanque de proceso | — |
| P-103 | **Bomba de agitación sumergible** | agitador AG-101, motorreductor M-101 | `MOTOR` |
| E-101 | **Resistencia de inmersión** | elemento calefactor, calentador | `RESISTENCIA` |
| P-102 | **Bomba de impulsión** | bomba de limpieza, de recirculación, de drenado, principal | `BOMBA` |
| SV-102 | **Electroválvula de llenado** | electroválvula 1 | `VALVULA1` |
| SV-103 | **Electroválvula de descarga** | electroválvula 2 | `VALVULA2` |
| SV-101 | **Se elimina** (no existe en el prototipo) | válvula solenoide de jabón | — |
| LSL-101 | **Interruptor de nivel bajo** | LIT-101 | `NIVEL1` |
| LSH-101 | **Interruptor de nivel alto** | LIT-101 | `NIVEL2` |
| TT-101 | **Transmisor de temperatura** (PT100 + 4–20 mA) | sensor de temperatura | `TEMPERATURA` |
| TK-103 | **Tanque de efluentes** | tanque de agua residual, de residuos | — |
| HV-101 | **Válvula manual de vaciado** de TK-103 | — | — |
| — | **Tubería de prueba** | circuito de prueba, línea a limpiar | — |
| — | **Detergente** | jabón, agente jabonoso, sustancia de limpieza | — |

---

## 4. Decisiones técnicas

### Proceso
- **Paso único:** no hay recirculación. P-102 vacía TK-102 a través de la tubería de prueba y el efluente termina en **TK-103**.
- TK-102 **se llena en cada fase**: **20–23 L** como máximo por fase (queda espacio libre arriba).
- **Consigna de temperatura: 35 °C** (preliminar) para **preenjuague y lavado**. El enjuague final va sin calentar.
  Justificación: el sello mecánico de la bomba falla por encima de 40 °C (riesgo R-11), así que se deja margen.
- **Agitación (P-103) solo antes de calentar**, no durante el calentamiento.
- **TK-103 se vacía a mano entre fases** (con HV-101). Solo hay 2 electroválvulas.
- **REQ-01 se redacta de nuevo:** cada fase es automática; entre fases el operario vacía manualmente TK-103. VAL-01 se ajusta igual.

### Programa
- Se documenta **el GRAFCET del equipo, corregido**, como diseño de la secuencia del corte 2 (incluye las 3 fases).
- El **Ladder v1** (`prueba1_cip`) queda como **primera implementación** (solo preenjuague y lavado).
- Pendiente de implementar en el PLC: enjuague final y pausa para que el operario vacíe TK-103.

### Componentes del prototipo
| Elemento | Decisión |
|---|---|
| Resistencia E-101 | Comprada como **1500 W**; a los 126 V del laboratorio entrega **≈ 2000 W**. **El modelo térmico usa 2000 W.** |
| Protecciones | Breaker de **15 A, 1 polo** (resistencia) y otro de **≈ 7 A** (bomba de impulsión y bomba de agitación). Ya no se usa el taco de 20 A. |
| SSR | **Dos:** 60 A para la resistencia y 40 A para la bomba de impulsión. **Sin disipador ni ventilador** (solo la placa metálica propia). |
| Bomba de impulsión P-102 | **Bomba periférica**, accionada por el SSR de 40 A. **Sin contactor ni guardamotor.** |
| Bomba de agitación P-103 | Sumergible, **110 V AC, 22 W**, dentro de TK-102, accionada por un relé externo con bobina de 24 V. |
| Dosificadora P-101 | Peristáltica de **12 V**, alimentada con un convertidor **LM2596**. |
| Electroválvulas | **Dos** (SV-102 llenado, SV-103 descarga), 24 V DC. |
| Nivel | **Un flotador doble** en TK-102 (LSL-101 y LSH-101). |
| Temperatura | **PT100 + transmisor 4–20 mA** con resistencia de **500 Ω** hacia la entrada analógica del PLC (de la universidad). |
| Tanques | TK-102: **verde, de plástico, de 50 L** (se llenan 20–23 L por fase); la resistencia atraviesa la pared con contratuerca y empaques. TK-103: **metálico de 30 L**. TK-101: pendiente. |
| Tubería | **PVC** de 1" y 3/4". |
| PLC y HMI | S7-1200 CPU 1214C AC/DC/RLY y HMI KTP600 (de la universidad). |
| Mando | Paro de emergencia, pulsadores, selector y pilotos (de la universidad). |
| No se usan / aún no | Motorreductor, ESP32, W5500, filtro Y, contactor, guardamotor. Aún no: manómetro, válvulas de bola, antirretorno. |

### Alimentación
- El PLC se alimenta a **110 V AC** del tomacorriente.
- Los **24 V DC** salen de una **fuente integrada en el banco** del laboratorio (no del PLC). De ahí se alimentan los sensores, el transmisor y las salidas de relé del PLC.
- Electroválvulas: el contacto de relé del PLC conmuta el **+24 V** de la fuente del banco hacia la bobina; el otro terminal va al **0 V** de la misma fuente.

### Comunicaciones
- **PLC → (protocolo S7) → Raspberry Pi con Node-RED → (HTTP) → API en AWS → interfaz en Streamlit.**
- PLC ↔ HMI por PROFINET.
- Reemplaza lo que decía el primer corte (ESP32, Modbus TCP, MQTT, ThingsBoard).
- IP del PLC y de la Raspberry: **pendientes** (las confirma Camilo).

### Matrices Pugh
- **Se quedan como diseño de referencia del primer corte.**
- Las diferencias con el prototipo se explican en **8.1 Cambios entre el diseño conceptual y el prototipo** (tabla con qué cambió y por qué).

### P&ID
- Se rehace con el glosario (borrador en TikZ, pendiente de revisión del equipo).

---

## 5. Pendientes por confirmar con el equipo

- [ ] Masa de agua del modelo térmico: 15 kg actual o 20–23 L reales.
- [ ] Consignas del plan de validación (ya no sirven 40 y 50 °C).
- [ ] Sobreimpulso máximo (con 15 % sobre 35 °C se llega a 40,25 °C, el límite del sello). *(Error ya decidido: ±1,75 °C.)*
- [ ] Valor del umbral de corte por sobretemperatura (en el documento queda "por definir").
- [ ] Termostato bimetálico: se cree que no se usa.
- [ ] Valor real del breaker de ≈ 7 A y voltaje de la red (126 V medidos).
- [ ] Protección de la bomba de impulsión si el SSR se queda pegado.
- [ ] Justificación de temperatura uniforme en el modelo sin agitación durante el calentamiento.
- [ ] Tanque de detergente (TK-101): cuál es y de cuántos litros.
- [ ] GRAFCET: qué sensor es SN1 y cuál SN2, qué significa "(N)" y los tiempos de los temporizadores.
- [ ] IP del PLC y de la Raspberry.
- [ ] Precios de lo comprado (para el presupuesto).

### Observaciones de seguridad para revisar
- A 126 V la resistencia consume **≈ 15,9 A**, más que el breaker de 15 A.
- Los SSR **sin disipador** pueden recalentarse (≈ 20 W de calor en el de la resistencia).
- Sin termostato, nada corta la resistencia si el SSR falla en cortocircuito.
