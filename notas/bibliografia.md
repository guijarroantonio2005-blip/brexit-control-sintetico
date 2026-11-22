## Abadie (2021). "Using Synthetic Controls: Feasibility, Data Requirements, and Methodological Aspects"

**Referencia:** Abadie, Alberto. 2021. "Using Synthetic Controls: Feasibility, Data Requirements, and Methodological Aspects." Journal of Economic Literature 59 (2): 391–425. 

**Idea principal:** Guía práctica sobre cuándo es viable el control sintético (requisitos de contexto y de datos), cómo diseñarlo y cómo comprobar su credibilidad con pruebas de robustez y diagnóstico.

**Contribución del autor:** Me aporta los requisitos y metodologías del uso del método utilizado para este trabajo.

## Springford (2023). "Are the costs of Brexit big or small?"

**Referencia:** Springford, J. (2023). *Are the costs of Brexit big or small?* CER Insight. Centre for European Reform.

**Idea principal:** la economía británica sería en torno a un 5 % menor por el Brexit, según su modelo de control sintético.

**Método:** donor pool de 22 economías avanzadas; el algoritmo elige los países y sus pesos para reproducir al Reino Unido en 2009-2016.

**Contribución del autor:** compara el control sintético con otros enfoques y defiende que es el menos malo.

## Du, Satoglu y Shepotylo (2023). "How did Brexit affect UK trade?"

**Referencia:** Du, J., Satoglu, E. B. y Shepotylo, O. (2023). How did Brexit affect UK trade? *Contemporary Social Science*, 18(2), 266-283.

**Idea principal:** ¿El TCA afectó al comercio exterior de UK? Las exportaciones de UK han bajado respecto a la UE y el resto del mundo. Las importaciones desde la UE se recuperaron; las del resto del mundo apenas se vieron afectadas, según el modelo SDID.

**Método:** Utilizan el SDID (método sintético de diferencias en diferencias).

**Contribución del autor:** Usan SDID, que consideran más eficiente que SC y DID, y comparan con ambos.

## Portes y Springford (2026). "The Impact of Brexit on UK Immigration and Labour Supply: Evidence from Synthetic Differences in Differences"

**Referencia:** Portes, J. & Springford, J. (2026). *The Impact of Brexit on UK Immigration and Labour Supply: Evidence from Synthetic Differences in Differences*. IZA Discussion Paper, 18478.

**Idea principal:** El Brexit significó más una reestructuración de la inmigración que un cambio cuantitativo.

**Método:** Utilizan el SDID (método sintético de diferencias en diferencias).

**Contribución del autor:** Señalan una limitación del control sintético de Alberto Abadie, ya que el *doppelgänger* debe tomar una correspondencia estrecha con la unidad tratada, ya sea debido a unas series previas breves o a grandes choques económicos que afectan a todas las unidades.

## Born, Müller, Schularick y Sedláček (2019). "The Costs of Economic Nationalism: Evidence from the Brexit Experiment"

**Referencia:** Benjamin Born, Gernot J. Müller, Moritz Schularick, Petr Sedláček, *The Costs of Economic Nationalism: Evidence from the Brexit Experiment*, The Economic Journal, Volume 129, Issue 623, October 2019, Pages 2722–2744.

**Idea principal:** El shock del Brexit empezó a dañar la economía británica inmediatamente tras el referéndum de 2016.

**Método:** Utilizan el método de control sintético de Abadie et al.

**Contribución del autor:** El método de control sintético apunta a efectos causales del Brexit, pero no explica cuáles fueron los indicadores que afectaron a su caída.

## Aportaciones a mi modelo

**Posibles distorsiones:**
1. Covid: los datos de 2020 podrían reflejar la pandemia y no solo el Brexit, y el donor pool podría verse afectado de forma desigual.
2. Las economías no pasan por el mismo periodo de tiempo; durante los años ha habido diferentes crisis y políticas internacionales que no afectan de la misma manera.

**Limitaciones del modelo:**
1. El control sintético no elimina el sesgo entre la comparación de los periodos pre y post entrenamiento. (Fuente: Du et al.)
2. Al tener una sola unidad tratada no podemos obtener estimaciones precisas, ya que la inferencia se basa en el método de placebo, el cual no es eficiente y cuyas propiedades estadísticas no se comprenden bien. (Fuente: Du et al.)

### Qué uso en mi proyecto
Método de control sintético de Alberto Abadie. 
**Periodo de tiempo: Entrenamiento y Validación**:
1. Fitting period 2000Q1-2012Q4: según Abadie debe haber un gran periodo previo a la intervención ya que el sesgo del estimador del control sintético es inversamente proporcional al número de periodos previos a la intervención.
2. Periodo de validación 2013Q1–2016Q2: Abadie utiliza el tramo restante a la intervención para evaluar la capacidad predictiva fuera de muestra de cada modelo.

**Países:** (Por definir) Usaré 29 economías de la OCDE. Obligado a quitar Irlanda, Abadie nos comenta que en el donor pool no debe de haber países que se hayan visto afectados por la política de la unidad tratada (Abadie, 2021). Mediante el método, a cada país deberemos de aportarle un peso $w_i \geq 0$ tal que la suma de todos los pesos debe ser igual a 1. (Abadie, 2021)

**Unidades macroeconómicas:** Para analizar la evolución económica, utilizaremos el PIB real per cápita expresado en volúmenes encadenados en moneda local ($LCU$, chain-linked volumes), lo que permite aislar el crecimiento real eliminando tanto el efecto de la inflación interna como las fluctuaciones del tipo de cambio. Con el fin de homogeneizar la escala y hacer comparables las trayectorias entre los distintos países del grupo de control, reescalaremos la serie mediante un índice con base $2000Q1 = 100$:

$$I_{j,t} = \frac{LCU_{j,t}}{LCU_{j,2000Q1}} \times 100$$

Además, como variables socioeconómicas eligiremos tasa de inversión, apertura comercial (dividida respecto al PIB), y tasa de inflación. Abadie utiliza estos mismos indicadores macroeconómicos en su ejemplo de Alemania (Abadie, 2021).

Para la inflación, calcularé el deflactor del PIB (PIB a precios corrientes entre PIB en volúmenes encadenados, por cien) y tomaré su variación interanual, promediada en el periodo de entrenamiento.

**Diseño e inferencia:** (Por estimar)

**Robustez:** Usaré el método de leave-one-out test. De esta manera podremos comprobar, de manera muy visual, la trayectoria de nuestro doppelganger y podremos decir que no depende de la presencia de un país específico

### Datos (Fuentes estadísticas)

**Referencia 1:** Organisation for Economic Co-operation and Development [OECD]. (2026). *Quarterly GDP and components - expenditure approach, national currency* [Dataset `OECD.SDD.NAD:DSD_NAMAIN1@DF_QNA_EXPENDITURE_NATIO_CURR(1.1)`]. OECD Data Explorer. https://data-explorer.oecd.org/

**Referencia 2:** Organisation for Economic Co-operation and Development [OECD]. (2026). *Quarterly population and employment, national concept* [Dataset `OECD.SDD.NAD:DSD_NAMAIN1@DF_QNA_POP_EMPNC(1.1)`]. OECD Data Explorer. https://data-explorer.oecd.org/

**Datos:** Se emplea un panel trimestral balanceado de **30 economías de la OCDE** desde `2000Q1` hasta `2024Q4` (100 trimestres en total: 52 trimestres de entrenamiento `2000Q1–2012Q4`, 14 trimestres de validación `2013Q1–2016Q2` y 34 trimestres post-referéndum `2016Q3–2024Q4`), extraído de *OECD Data Explorer*:
* **Cuentas Nacionales Trimestrales (`DF_QNA_EXPENDITURE_NATIO_CURR`):** PIB (`B1GQ`), formación bruta de capital (`P5`), exportaciones (`P6`) e importaciones (`P7`) en moneda nacional, ajustados por estacionalidad y calendario (`ADJUSTMENT = Y`), tanto en volúmenes encadenados (`L`) como a precios corrientes (`V`).
* **Población Trimestral (`DF_QNA_POP_EMPNC`):** Población total (`POP`, en miles de personas) para expresar el PIB real en términos per cápita.
