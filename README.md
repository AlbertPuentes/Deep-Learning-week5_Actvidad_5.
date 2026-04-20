# Deep-Learning-week5_Actvidad_5.

# Red Neuronal para Clasificación Multiclase: Impacto de Hiperparámetros y Optimización

**Objetivo:** Implementar una red neuronal sin convoluciones para clasificar el dataset MNIST, comparando el comportamiento del entrenamiento bajo dos configuraciones distintas de optimización.

**Configuraciones a comparar:**
* **Configuración 1:** Optimizador **Adam** con Tasa de Aprendizaje (LR) = 0.001
* **Configuración 2:** Optimizador **SGD** (Descenso de Gradiente Estocástico) con Tasa de Aprendizaje (LR) = 0.01

*Nota: Se mantendrá constante la arquitectura de la red, el tamaño de lote (batch size = 64) y el número de épocas (epochs = 10).*

## Análisis y Conclusiones

Basado en la gráfica comparativa y los registros del entrenamiento, podemos observar las siguientes diferencias clave entre las dos configuraciones:

1. **Velocidad de Convergencia:** * **Adam** converge significativamente más rápido en las primeras épocas. Alcanza una precisión alta y una pérdida baja desde la época 2 o 3.
   * **SGD** tiene una curva de aprendizaje mucho más suave y lenta. Necesita más épocas para acercarse al rendimiento que Adam logra inicialmente.

2. **Estabilidad:**
   * **SGD** demuestra ser bastante estable. La caída en su función de pérdida es constante y predecible a lo largo de las iteraciones.
   * **Adam** también es estable en este problema sencillo, pero en el gráfico de pérdida de validación a veces se pueden notar ligeras fluctuaciones al final de las épocas, dado que su ajuste adaptativo de la tasa de aprendizaje puede llevarlo a "saltar" un poco una vez que se acerca al mínimo global.

3. **Hallazgos sobre los Optimizadoress:**
   * El optimizador adaptativo (**Adam**) ajusta dinámicamente la tasa de aprendizaje por cada parámetro, lo que es ideal para superar "mesetas" rápidamente y por eso su loss inicial cae en picada.
   * Por otro lado, **SGD** clásico con un learning rate fijo de `0.01` requiere muchas más iteraciones para actualizar los pesos significativamente. Si aumentáramos el *learning rate* de SGD a un valor muy alto (ej. `0.5`), podríamos acelerarlo, pero correríamos el riesgo de generar oscilaciones inestables (divergencia).
   * **Conclusión general:** Para este tipo de red MLP multicapa estándar, Adam ofrece un excelente compromiso de velocidad sin requerir un ajuste minucioso de la tasa de aprendizaje, ahorrando tiempo computacional (épocas) respecto a un SGD estándar.
