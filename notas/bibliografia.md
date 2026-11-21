## Springford (2023). "Are the costs of Brexit big or small?"

**Referencia:** Springford, J. (2023). *Are the costs of Brexit big or small?* CER Insight. Centre for European Reform.

**Idea principal:** la economía británica sería en torno a un 5 % menor por el Brexit, según su modelo de control sintético.

**Método:** donor pool de 22 economías avanzadas; el algoritmo elige los países y sus pesos para reproducir al Reino Unido en 2009-2016.

**Contribución del autor:** compara el control sintético con otros enfoques y defiende que es el menos malo.

## J. Du, E. B. Satoglu, O. Shepotylo (2023). "How did Brexit affect UK trade?"

**Referencia:** Jun Du & Emine Beyza Satoglu & Oleksandr Shepotylo, 2023. "How did Brexit affect UK trade?," Contemporary Social Science, Taylor & Francis Journals, vol. 18(2), pages 266-283, March. 

**Idea principal:** ¿El TCA afectó al comercio exterior de UK? Las exportaciones de UK han bajado respecto a la UE y el resto del mundo. as importaciones desde la UE se recuperaron; las del resto del mundo apenas se vieron afectadas, según el modelo SDID.

**Método:** Utilizan el SDID (método sintético de diferencias en diferencias).

**Contribución del autor:** Usan SDID, que consideran más eficiente que SC y DID, y comparan con ambos.

## Portes y Springford (2026). "The Impact of Brexit on UK Immigration and Labour Supply: Evidence from Synthetic Differences in Differences"

**Referencia:** Portes, J. & Springford, J. (2026). *The Impact of Brexit on UK Immigration and Labour Supply: Evidence from Synthetic Differences in Differences*. IZA Discussion Paper, 18478.

**Idea principal:** El Brexit significó más una reestructuración de la inmigración que un cambio cuantitativo.

**Método:** Utilizan el SDID (método sintético de diferencias en diferencias).

**Contribución del autor:** Critican al modelo de Alberto Abadie, ya que el *doppelgänger* debe tomar una correspondencia estrecha con la unidad tratada, ya sea debido a unas series previas breves o a grandes choques económicos que afectan a todas las unidades.

## Born, Müller, Schularick y Sedláček (2019). "The Costs of Economic Nationalism: Evidence from the Brexit Experiment"

**Referencia:** Benjamin Born, Gernot J. Müller, Moritz Schularick, Petr Sedláček, *The Costs of Economic Nationalism: Evidence from the Brexit Experiment*, The Economic Journal, Volume 129, Issue 623, October 2019, Pages 2722–2744.

**Idea principal:** El shock del Brexit empezó a dañar la economía británica inmediatamente tras el referéndum de 2016.

**Método:** Utilizan el método de control sintético de Abadie et al.

**Contribución del autor:** El método de control sintético apunta a efectos causales del Brexit, pero no explica cuáles fueron los indicadores que afectaron a su caída.

## Aportaciones a mi modelo

**Posibles distorsiones:**
1. Covid: los datos de 2020 podrían reflejar la pandemia y no solo el Brexit, y el donor pool podría verse afectado de forma desigual.
2. Las economías no pasan por el mismo periodo de tiempo; durante los años ha habido diferentes crisis y políticas internacionales que no afectan de la misma manera.

**Críticas al método:**
1. El control sintético no elimina el sesgo entre la comparación de los periodos pre y post entrenamiento. (Fuente: Du et al.)
2. Al tener una sola unidad tratada no podemos obtener estimaciones precisas, ya que la inferencia se basa en el método de placebo, el cual no es eficiente y cuyas propiedades estadísticas no se comprenden bien. (Fuente: Du et al.)

**Qué uso en mi proyecto:** método de control sintético de Alberto Abadie, periodo de entrenamiento 2000-2016.
**Decisión pendiente (Diseño e Inferencia):**
* **Opción 1 — Nivel Nacional ($N_{tr}=1$, PIB agregado del Reino Unido):** Más directo y manejable en datos. Se estima el Control Sintético clásico y el SDID como análisis de robustez, realizando la inferencia estadística mediante pruebas de **placebo** (en el espacio y en el tiempo).
* **Opción 2 — Nivel Regional ($N_{tr}=12$, Regiones del Reino Unido frente a regiones europeas/OCDE):** Requiere mayor esfuerzo de recolección y armonización de datos (ej. OECD Regional Database TL2 o Eurostat), pero al contar con múltiples unidades tratadas permite aplicar la inferencia **Jackknife** en el SDID y superar las limitaciones estadísticas del caso $N_{tr}=1$.

**Datos:** (A confirmar).