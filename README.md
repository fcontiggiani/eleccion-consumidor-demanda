# Elección óptima del consumidor bajo distintas formas funcionales

Simulador interactivo para la enseñanza de teoría del consumidor a nivel de grado avanzado (Economía, Contador Público, Administración). Permite explorar el problema de maximización de utilidad sujeta a restricción presupuestaria, comparar cuatro formas funcionales de preferencias racionales y derivar en tiempo real la curva precio-consumo y la función de demanda marshalliana correspondiente.

[`*Demo en vivo*`](https://fcontiggiani.github.io/eleccion-consumidor-demanda/eleccion_consumidor_demanda.html)

---

## Qué hace

El consumidor resuelve

$$\max_{x,y\ge0} \; U(x,y) \quad \text{s.a.} \quad p_x x + p_y y = m$$

para cuatro formas funcionales seleccionables, cada una con su propio conjunto de parámetros y su propio tratamiento analítico:

| Forma funcional | $U(x,y)$ | Parámetros ajustables | Naturaleza de la solución |
|---|---|---|---|
| **Cobb-Douglas** | $x^{\alpha}y^{\beta}$ | $\alpha,\beta$ **independientes** (no normalizados a $\alpha+\beta=1$) | Interior, por tangencia |
| **Sustitutos perfectos** | $ax+by$ | $a,b$ | De esquina, por comparación de utilidad marginal por peso |
| **Complementarios perfectos (Leontief)** | $\min(x/a,\,y/b)$ | $a,b$ | Interior, en el vértice no diferenciable de la curva en L |
| **CES** | $(\alpha x^{\rho}+(1-\alpha)y^{\rho})^{1/\rho}$ | $\alpha\in(0,1)$, $\rho$ | Interior, por tangencia; nidifica a las tres formas anteriores como casos límite |

La familia CES converge a Cobb-Douglas cuando $\rho\to0$, a sustitutos perfectos cuando $\rho\to1$ y a Leontief cuando $\rho\to-\infty$, lo que permite mostrar en un único control deslizante ($\rho$, equivalentemente la elasticidad de sustitución $\sigma=1/(1-\rho)$) el espectro completo de sustituibilidad entre bienes.

### Un detalle deliberado: Cobb-Douglas con $\alpha+\beta\neq1$

A diferencia de la exposición habitual de los manuales, el simulador **no normaliza** los exponentes de Cobb-Douglas. Esto permite verificar interactivamente un resultado que suele generar confusión: la canasta óptima depende únicamente de la *razón* $\alpha/\beta$, nunca de la suma $\alpha+\beta$, porque $U^{1/(\alpha+\beta)}$ es una transformación monótona de $U$ y representa exactamente las mismas preferencias. El panel de resultados muestra $\alpha+\beta$ y las participaciones de gasto resultantes para hacer explícita esta invariancia.

---

## Componentes de la interfaz

1. **Selector de forma funcional**, con controles que se adaptan al modelo elegido: solo se muestran los parámetros pertinentes a cada forma.
2. **Panel 1 — Óptimo del consumidor**, en el plano $(x,y)$: curva(s) de indiferencia, restricción presupuestaria y punto óptimo. El botón *"Fijar punto actual en el mapa"* permite superponer hasta cinco óptimos (cada uno conserva su propia forma funcional y parámetros) para comparar escenarios de precios o ingreso en una misma vista.
3. **Panel 2 — Curva precio-consumo**, que traza el lugar geométrico de óptimos al barrer $p_x$ o $p_y$ (seleccionable con un interruptor), con manejo correcto de la discontinuidad que produce el caso de sustitutos perfectos.
4. **Panel 3 — Función de demanda**, en el espacio (precio, cantidad), en correspondencia punto a punto con la curva precio-consumo del panel anterior.
5. **Bloque de resultados numéricos**: canasta óptima, utilidad alcanzada, gasto y participación de cada bien, relación marginal de sustitución en el óptimo, elasticidad-precio propia (analítica cuando existe forma cerrada constante; numérica en caso contrario) y el tipo de solución (interior o de esquina).
6. **Derivación analítica desplegable** (colapsada por defecto): desarrollo completo del Lagrangiano —o el razonamiento correspondiente en los casos no diferenciables de sustitutos perfectos y Leontief— con condiciones de primer orden, condición de tangencia o de esquina, y obtención de las funciones de demanda marshallianas, recalculado íntegramente al cambiar de forma funcional.

---

## Uso en clase

- Alternar entre formas funcionales manteniendo $p_x,p_y,m$ fijos permite mostrar cómo distintas preferencias producen curvas precio-consumo cualitativamente distintas: horizontal (Cobb-Douglas), función escalón con salto discreto (sustitutos perfectos), o recta con pendiente fija coincidente con la senda de expansión (Leontief).
- El slider $\rho$ de CES es útil para una demostración progresiva: partiendo de $\rho\approx0$ (Cobb-Douglas) y desplazándolo hacia $\rho\to1$ o hacia valores muy negativos, se observa en vivo la transición hacia sustitutos perfectos o hacia complementarios perfectos, respectivamente.
- Recomendado para las clases de **Consumidor** y **Demanda, Oferta y Mercado** de un curso de microeconomía intermedia.

---

### Incrustación en Moodle

**Opción recomendada — recurso de tipo URL:** pegar el enlace anterior como recurso externo; es la alternativa de mayor compatibilidad, independiente de la configuración de seguridad de la instalación institucional.

## Notas técnicas

- **Sin dependencias de compilación.** Archivo HTML único, abrible directamente en cualquier navegador moderno con JavaScript habilitado.
- **Graficación:** SVG nativo generado dinámicamente en JavaScript vainilla; no se emplean librerías de charting externas.
- **Notación matemática:** MathJax 3, cargado desde `cdnjs.cloudflare.com`, con configuración explícita de delimitadores `$...$` (no activos por defecto en MathJax 3).
- **Sin frameworks de frontend** (sin React, sin build step): toda la lógica reside en un único bloque `<script>`.
- Responsive hasta un ancho mínimo de aproximadamente 380 px; el layout de dos columnas (controles + gráficos) colapsa a una columna en pantallas angostas.

---

## Fundamentación teórica

La notación y el tratamiento siguen el estándar de Varian, *Intermediate Microeconomics*, y Mas-Colell, Whinston y Green, *Microeconomic Theory*, para la parte de teoría del consumidor con preferencias CES, sustitutos perfectos y complementarios perfectos.

---

## Licencia y uso

Material de libre uso y adaptación para fines docentes. Se agradece atribución si se redistribuye o modifica.
