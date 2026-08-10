# Contenido pendiente de las semanas 14 y 15

Este material vivia dentro de `index.html` cuando cada pestaña semanal cargaba
su propio contenido. Al pasar las pestañas a modo lanzador, se guarda aquí para
poder armar `w14_onepager.html` y `w15_onepager.html` cuando toque.
Borra este archivo una vez que esos dos one-pagers estén publicados.


---

## Semana 14. Introducción a la Gestión de Portafolios de Renta Fija

*Sesiones: 9 y 12 de noviembre de 2026*

### Resumen

Semana de integración: todos los conceptos del curso convergen en el marco de gestión de portafolios. Se contrasta la gestión pasiva (pure index matching, enhanced indexing) con la activa (duration positioning, sector rotation, yield curve strategies, security selection). La inmunización clásica exige D_activos = D_pasivos y PV(activos) ≥ PV(pasivos) para garantizar la cobertura de un pasivo ante movimientos paralelos. El framework de Liability-Driven Investing (LDI) para fondos de pensiones extiende este concepto. Las estrategias de yield curve (barbell vs. bullet vs. ladder) se evalúan bajo distintos escenarios de movimiento. La atribución de retorno descompone el alpha del gestor y el VaR/ES cuantifican la pérdida máxima esperada con un nivel de confianza dado.

### Keywords

- Immunization
- Liability-Driven Investing (LDI)
- Return Attribution
- VaR / Expected Shortfall
- Pure Index Matching
- Enhanced Indexing
- Barbell vs. Bullet vs. Ladder
- Tracking Error
- Information Ratio
- Cash Flow Matching
- Contingent Immunization
- Stress Testing

### Conceptos clave

- **Pure index matching:** el Bloomberg US Aggregate tiene 12,000+ emisiones. Imposible replicar perfectamente por iliquidez → enhanced indexing: igualar los risk factors (duration, KRDs, sector allocation, calidad crediticia) con un subconjunto eficiente.

- **Inmunización clásica:** condiciones: \((1)\; D_A = H\) (duration activos = horizonte) y \((2)\; PV_A \geq PV_P\). Protege solo ante parallel shifts. Para non-parallel se necesita cash flow matching o multi-factor immunization.

- **Barbell vs. bullet:** barbell concentra en extremos de curva → mayor convexity, beneficia ante curva que se aplana (bull flattening). Bullet concentra alrededor del duration objetivo → beneficia ante curva plana o movimientos paralelos.

- **Atribución de retorno:** 

\[R_{\text{total}} = \underbrace{\text{Yield income}}_{\text{carry}} + \underbrace{\text{Roll-down}}_{\text{curva}} + \underbrace{\Delta P(\Delta y)}_{\text{tasa}} + \underbrace{\Delta P(\Delta s)}_{\text{spread}} + R_{\text{FX}}\]

 Separa cuánto del retorno viene de carry, gestión activa, y movimiento de mercado.

- **VaR y ES:** \(\text{VaR}_{95\%}\) = máxima pérdida que no se excede el 95% del tiempo. \(\text{ES} = E[\text{Pérdida} \mid \text{Pérdida} > \text{VaR}]\). Siempre \(ES > \text{VaR}\); es la medida preferida bajo Basel III.

### Aplicación práctica

- Construir portafolio inmunizado ante un pasivo en S5
- Atribuir retorno mensual de un portafolio vs. benchmark
- Calcular VaR de tasa ante +100bps paralelo

### Conexiones del curso

- Todas las semanas: integración total del curso
- S3–S4: Duration y KRDs como inputs de gestión
- S12: Derivatives overlay para ajustar duration sin vender bonos


---

## Semana 15. Mercado Peruano de Renta Fija

*Sesiones: 16 y 19 de noviembre de 2026*

### Resumen

La semana final contextualiza todos los conceptos del curso en el mercado peruano de renta fija, uno de los más desarrollados de América Latina. El Ministerio de Economía y Finanzas (MEF) emite bonos soberanos en soles (nominales y VAC , ajustados por inflación, ) y en dólares (Global Bonds). El BCRP administra la política monetaria y emite Certificados de Depósito como instrumento de esterilización. La Bolsa de Valores de Lima (BVL) opera el mercado secundario; CAVALI es el depósito central de valores. Se analiza la curva soberana peruana (en PEN y USD), el riesgo país (EMBIG spread Perú), y los instrumentos corporativos locales. Perú tiene grado de inversión (BBB por S&P, Baa1 por Moody's) y una curva en soles que va desde letras del Tesoro de corto plazo hasta bonos soberanos a 40 años.

### Keywords

- Bonos Soberanos Peruanos
- VAC (Valor Adquisitivo Constante)
- Global Bonds Perú
- EMBIG Spread Perú
- Curva en Soles
- Curva en USD
- BCRP CD
- BVL / CAVALI
- Letras del Tesoro
- MEF
- Rating BBB / Baa1
- Riesgo País
- AFP (Fondos de Pensiones)

### Conceptos clave

- **Estructura de la curva soberana peruana:** MEF emite bonos en PEN a plazos de 2, 3, 5, 7, 10, 12, 15, 20, 30 y 40 años. La curva en USD con Global Bonds (5, 10, 30 años) es el benchmark para el crédito soberano internacional.

- **VAC (Bonos en Valor Adquisitivo Constante):** análogos peruanos de los TIPS. El principal se ajusta por el índice de precios al consumidor (IPC). El yield real peruano histórico ha estado entre 2.5–4.5% (real). Referencia para AFP y aseguradoras.

- **EMBIG Spread Perú:** mide el diferencial de riesgo soberano de Perú sobre Treasuries de EE.UU. Históricamente entre 80–200bps en el ciclo normal; se amplió a 300+bps durante COVID-19 y crisis política 2022.

- **AFP como demanda dominante:** los fondos de pensiones privados (AFP) son los mayores tenedores de bonos soberanos locales, especialmente VAC de largo plazo (liability-driven). Su restricción regulatoria de duration crea nichos de valor relativo.

- **Mercado corporativo local:** instrumentos de corto plazo (papeles comerciales, CDBCRP) y largo plazo (bonos de arrendamiento financiero, bonos corporativos). Liquidez menor que el soberano; spread sobre curva soberana de 50–300bps dependiendo del emisor.

### Aplicación práctica

- Construir la curva soberana peruana en PEN con datos del MEF
- Calcular breakeven de inflación (bono nominal vs. VAC)
- Analizar el riesgo de un portafolio AFP ante +100bps paralelo en curva PEN

### Aplicación de todo el curso

- S1–S2: Los bonos soberanos peruanos tienen todos los features estudiados
- S5: La curva peruana tiene sus propias teorías (demanda AFP, política BCRP)
- S10: VAC como el TIPS peruano (breakeven inflation)
- S14: Las AFPs son el ejemplo institucional más claro de LDI local

