## Descripción general

La carpeta codigo contiene todos los scripts y notebooks desarrollados para el análisis numérico y la implementación del modelo predictivo del proyecto.

## Contenido

Scripts en Python encargados de:

- Carga y limpieza del dataset.
- Cálculo de estadísticas descriptivas.
- Normalización de datos.
- Construcción del sistema normal de mínimos cuadrados.
- Implementación de métodos numéricos (Gauss, Gauss-Jordan, LU, Jacobi, Gauss-Seidel).
- Evaluación de métodos, generación de predicciones y análisis de resultados.

## Estructura y buenas

El código fue organizado de manera modular, definiendo funciones independientes para cada etapa del proceso. Esta estructura permite:

- Ejecutar pruebas aisladas por función.
- Facilitar la lectura y mantenimiento del código.
- Comparar distintos métodos numéricos sobre un mismo sistema algebraico.

### Resultados del proyecto

Según los resultados del modelo numérico de regresión lineal, la importancia de las variables se define por la magnitud absoluta de sus **coeficientes ($\beta$)**. Estos valores actúan como el "peso" o porcentaje de influencia que cada factor ejerce sobre la probabilidad de victoria.

Las variables más determinantes, clasificadas por su impacto absoluto ($|\beta|$), son:

### Top 3 Variables Más Importantes

1.  **Daño Total Recibido (`total_damage_taken`)**
    *   **Peso (Coeficiente):** **0.3738**
    *   **Impacto:** Es la variable más influyente del sistema, pero tiene una correlación **negativa**. Esto indica que recibir grandes cantidades de daño es el indicador más fuerte de una **derrota**. Cuanto más daño recibe un equipo, menor es su probabilidad de ganar.

2.  **Daño a Torres (`damage_dealt_to_turrets`)**
    *   **Peso (Coeficiente):** **0.2979**
    *   **Impacto:** Es el predictor **positivo** más fuerte. Destruir estructuras defensivas es la condición de victoria mecánica más importante, superando incluso al oro o a las *kills*.

3.  **Oro Ganado (`gold_earned`)**
    *   **Peso (Coeficiente):** **0.1797**
    *   **Impacto:** Actúa como el combustible del equipo. Aunque es crucial, el modelo matemático revela que es menos determinante que los objetivos estructurales (torres) o la resistencia en combate (daño recibido).

---

### Ranking Completo de Importancia (Pesos del Modelo)

La siguiente tabla muestra la jerarquía exacta calculada por el algoritmo de Eliminación Gaussiana. Los coeficientes provienen de datos normalizados, lo que permite comparar directamente su "porcentaje" de importancia relativa:

| Ranking | Variable (Factor de Macrojuego) | Coeficiente ($\beta$) | Interpretación del Impacto |
| :--- | :--- | :--- | :--- |
| **1** | **Total Damage Taken** | **-0.37382** | **Muy Alto (Negativo):** Recibir daño reduce drásticamente la victoria. |
| **2** | **Damage Dealt to Turrets** | **0.29791** | **Muy Alto (Positivo):** Prioridad estratégica #1 para ganar. |
| **3** | **Gold Earned** | **0.17971** | **Alto (Positivo):** Ventaja económica fundamental. |
| 4 | Total Damage Dealt to Champs | 0.15941 | **Medio (Positivo):** La agresión efectiva suma, pero menos que las torres. |
| 5 | Vision Score | -0.05760 | **Bajo (Negativo):** Curiosamente, un puntaje excesivo correlaciona levemente con perder (posiblemente por jugar a la defensiva). |
| 6 | Baron Kills | 0.02319 | **Marginal:** Impacto bajo en el modelo lineal global. |
| 7 | Dragon Kills | 0.01494 | **Marginal:** Menor peso individual que el Barón. |
| 8 | Wards Placed | -0.01236 | **Insignificante:** Poner wards por sí solo no garantiza nada. |
| 9 | Wards Killed | 0.00361 | **Insignificante:** Impacto casi nulo. |
| 10 | Champion Mastery | -0.00253 | **Nulo:** La maestría previa no afecta el resultado de la partida actual. |

*Fuente de datos: Tabla de coeficientes calculados con Gauss (pivoteo parcial) en el código final.*

### Análisis de los Resultados
El modelo desmiente la creencia común de que los objetivos neutrales (Barón y Dragón) son lo más importante; matemáticamente, su peso (~0.02) es mínimo comparado con la presión en estructuras (~0.30) o la economía (~0.18). El sistema sugiere que **no morir (evitar daño recibido) y destruir torres** son las verdaderas claves estadísticas para la victoria en el servidor EUN1.