# Jimenez_Adolfo_Montecarlo
S20 - Módulo 1. Actividad didáctica 2-M1
# 🎲 Yahtzee con Montecarlo y Ley de los Grandes Números

## 🎥 Video Explicativo de la Actividad

> 📺 **[Haz clic aquí para ver el video de sustentación del proyecto]([[PEGA_AQUI_EL_ENLACE_DE_TU_VIDEO](https://drive.google.com/file/d/1BYs_VDYRSkfOVMFKOAtERYkxe4dWXbUU/view?usp=sharing)]**  
---

Proyecto de simulación estocástica del juego de Yahtzee para 2 jugadores utilizando **Muestreo de Montecarlo** (estimación de Valor Esperado, $EV$) y validación empírica de la **Ley de los Grandes Números (LGN)**.

---

## 🛠️ Modificaciones y Aportes sobre el Código Base

Sobre la plantilla original suministrada por el docente, se desarrollaron las siguientes mejoras y extensiones:

### 1. Correcciones de Sintaxis y Reglas Oficiales
* **Sección Superior:** Corrección del cálculo de puntuación para prevenir excepciones de clave ausente (`counts.get(num, 0) * num`).
* **Bono Superior (+35 pts):** Implementación del cálculo oficial que otorga 35 puntos adicionales al acumular $\ge 63$ puntos en las categorías de unos a seises.
* **Categoría Full House:** Corrección para validar combinaciones de 5 dados iguales (*Yahtzee* comodín) con 25 puntos reglamentarios.
* **Registro de dados:** Ajuste en el conteo de relanzamientos (*rerolls*) para contabilizar únicamente los dados efectivamente arrojados en cada tirada.

### 2. Optimización Computacional (Motor Montecarlo)
* **Precomputación de combinaciones:** Generación estática de las 32 máscaras de retención ($2^5$) al inicio del programa.
* **Poda analítica de rollouts:** Evaluación directa en $O(1)$ sin simulaciones estocásticas cuando la máscara retiene los 5 dados o restan 0 tiradas.
* **Mutación in-place:** Reemplazo de copias redundantes de listas en memoria por actualización directa de dados relanzados.

### 3. Benchmark de Rendimiento (Validación Experimental)
* Prueba de esfuerzo independiente variando las muestras por máscara ($N \in [50, 400]$)[cite: 3].
* Comprobación de una ventaja creciente en cargas exigentes ($N = 200$ a $400$), logrando un ahorro de tiempo de cómputo sostenido de entre **12.8% y 15.9%** (y **12.3%** en $N = 50$)[cite: 3].

### 4. Módulo de Visualización y Análisis Didáctico (LGN)
Diseño de un panel gráfico multiparámetro en Seaborn/Matplotlib[cite: 2]:
* **Marcador comparativo:** Puntuaciones logradas por cada jugador en las 13 categorías (Jugador 1: **91 pts** vs. Jugador 2: **135 pts**)[cite: 2].
* **Opción A (Dinámica temporal — 1 Partida):** Trayectoria acumulada tiro a tiro sobre **323 dados lanzados**, evidenciando cómo la dispersión inicial disminuye al acumular historial (error absoluto medio de **1.19%**)[cite: 2].
* **Opción B (Límite asintótico — 60 Partidas):** Histograma de frecuencias relativas con **19,703 lanzamientos acumulados**, convergiendo a la línea teórica del $16.67\%$ con un error absoluto medio reducido a **0.35%**[cite: 2].

### 5. Exportación Automatizada y Documentación Académica
* **Exportación de entregables:** Generación automática de gráficos en alta resolución (`analisis_lgn_yahtzee.png` a 300 DPI) y respaldos tabulares (`puntuaciones_partida.csv` y `validacion_dados_lgn.csv`).
* **Informe Universitario (`informe_universitario_yahtzee.html`):** Documento académico maquetado en HTML5/CSS3 con análisis descriptivo de resultados, tablas estadísticas e interpretación pedagógica de la LGN.

---
