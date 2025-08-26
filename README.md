# Simulador de Estimadores Estadísticos para U{1, ..., θ}

Una herramienta web interactiva para la simulación, comparación y visualización del rendimiento de estimadores estadísticos en el contexto del problema de estimación de un máximo poblacional.

> **Visualización Principal:** La aplicación presenta un panel de control a la izquierda para configurar los parámetros de la simulación. El área principal muestra un gráfico de barras comparando el Error Cuadrático Medio (ECM) de cada estimador, un histograma detallado de la distribución de las estimaciones y una tabla con métricas de rendimiento (sesgo, varianza, ECM).

**Demo en Vivo:** [Github pages pronto] 
---

## Contexto del Problema: "Situación 3"

Este proyecto implementa una solución al siguiente problema de estadística inferencial:

> En una población hay un número $\theta$ desconocido de vehículos informales ("piratas"), numerados consecutivamente $1, 2, 3, ..., \theta$. Con el propósito de estimar $\theta$, se registra una muestra aleatoria de tamaño $n$. El objetivo es simular y evaluar el comportamiento de diferentes estimadores para $\theta$, comparándolos especialmente en cuanto a Sesgo, Varianza y Error Cuadrático Medio (ECM).

### Estimadores Implementados

La simulación evalúa los siguientes estimadores propuestos, además de un estimador de referencia (UMVU) para un análisis más completo.

| Identificador | Estimador (Fórmula) | Lógica Principal |
| :--- | :--- | :--- |
| **e1** | $\hat{\theta}_{(1)} = 2\bar{X}_n - 1$ | Basado en el **momento de primer orden** (la media muestral). Proyecta el centro de la muestra para estimar el extremo. |
| **e2** | $\hat{\theta}_{(2)} = X_{(n)} + X_{(1)} - 1$ | Utiliza los **valores extremos** de la muestra (el máximo y el mínimo) para estimar el rango completo de la población. |
| **e3** | $\hat{\theta}_{(3)} = X_{(n)} + \frac{X_{(n)} - X_{(1)}}{n-1}$ | Se basa en el **máximo observado** y le añade un término de corrección basado en el espaciado promedio entre muestras. |
| **e4**| $\hat{\theta}_{(4)} = 2Me(X) - 1$ | Similar al primer estimador, pero usa la **mediana** en lugar de la media, haciéndolo más robusto a valores atípicos. |
| **e5**| $\hat{\theta}_{(5)} = \bar{X} + 3S$ | Un enfoque empírico que utiliza la media más tres **desviaciones estándar** para tratar de cubrir la mayor parte de la distribución. |

---

## Características Detalladas

### Núcleo de Simulación y Análisis
* **Motor de Monte Carlo:** El corazón de la aplicación es un motor de simulación robusto escrito en JavaScript puro que ejecuta miles de réplicas para evaluar el comportamiento a largo plazo de los estimadores.
* **Reproducibilidad Garantizada:** La implementación de una **semilla** para el generador de números pseudoaleatorios asegura que los resultados sean 100% reproducibles si se usan los mismos parámetros de entrada.
* **Métricas Clave:** Calcula y presenta de forma clara las tres métricas de rendimiento solicitadas en el problema: **Sesgo**, **Varianza** y **Error Cuadrático Medio (ECM)**.

### Visualización de Datos e Interfaz
* **Panel de Control Interactivo:** Permite al usuario modificar en tiempo real los parámetros fundamentales de la simulación:
    - `θ`: El verdadero tamaño de la población.
    - `n`: El tamaño de la muestra a extraer.
    - `R`: El número de réplicas de la simulación.
* **Gráficos Dinámicos:** Renderizados con HTML5 Canvas para un rendimiento óptimo, los gráficos permiten:
    - Comparar el ECM de todos los estimadores para identificar rápidamente al de mejor rendimiento.
    - Analizar la distribución de las estimaciones de cualquier estimador mediante un histograma detallado.
* **Interpretación Automática:** Una característica destacada que genera un análisis en texto plano sobre los resultados, contextualizándolos en un escenario práctico y ofreciendo conclusiones y recomendaciones.

---

## Guía de Uso

El proyecto es completamente autocontenido. No requiere dependencias, un proceso de compilación ni un servidor web.

1.  **Descargar:** Clona o descarga el repositorio que contiene el archivo `index.html`.
2.  **Abrir:** Abre el archivo `index.html` directamente en un navegador web moderno (ej. Google Chrome, Firefox, Edge).
3.  **Interactuar:**
    * Utiliza los controles en la sección "Parámetros y opciones" para configurar tu escenario.
    * Selecciona los estimadores que deseas incluir en la simulación.
    * Presiona "Simular" para ejecutar el análisis y observar los resultados.

---

## Arquitectura y Tecnologías

El proyecto fue desarrollado con un enfoque minimalista, utilizando tecnologías web estándar sin recurrir a frameworks externos.

* **HTML5:** Para la estructura y semántica del documento.
* **CSS3:** Para el diseño visual, utilizando variables CSS para la tematización y un diseño responsivo.
* **JavaScript (Vanilla):** Para toda la lógica de la aplicación, desde la simulación hasta la manipulación del DOM y el renderizado de los gráficos.

El flujo de la aplicación se puede resumir de la siguiente manera:
[ Parámetros de Entrada (HTML UI) ]
|
v
[ Motor de Simulación y Análisis (JavaScript) ]
|
v
[ Resultados Visuales (HTML Table & Canvas) ]

---

## Licencia

Este proyecto se distribuye bajo la **Licencia MIT**.