# Megaline parte 2: clasificación de planes móviles

## Contexto
Este repositorio continúa el proyecto original de Megaline. En esta segunda parte se amplía el análisis previo para profundizar en las herramientas utilizadas, comparar modelos de clasificación y documentar de forma más completa el proceso.

## Descripción
Megaline quiere migrar a sus clientes a los planes "Smart" y "Ultra". Para ello se analiza el comportamiento mensual de los usuarios —llamadas, minutos, mensajes y tráfico de datos— con el objetivo de recomendar el plan más adecuado.

## Objetivo
Construir un modelo de clasificación que, con una exactitud mínima de 0.75, determine si un cliente debería contratar el plan **Ultra** (`is_ultra = 1`) o permanecer con **Smart** (`is_ultra = 0`).

## Datos
El archivo `users_behavior.csv` contiene 3 214 registros con las columnas:
- `calls`: número de llamadas realizadas en el mes
- `minutes`: duración total de las llamadas
- `messages`: cantidad de SMS enviados
- `mb_used`: tráfico de internet en megabytes
- `is_ultra`: indicador binario del plan contratado

## Herramientas empleadas
- **pandas** y **NumPy** para la manipulación de datos
- **matplotlib** y **seaborn** para la visualización
- **scikit-learn** para los algoritmos de aprendizaje automático

## Mejoras buscadas
- Mayor detalle sobre las herramientas empleadas y su papel en el flujo de trabajo
- Evaluación de distintos modelos y ajuste de hiperparámetros para mejorar la exactitud
- Documentación más completa para facilitar la reproducción del análisis

## Modelos entrenados
1. **Árbol de decisión**: se evaluaron profundidades de 1 a 10. El mejor árbol tuvo `max_depth=7` con una exactitud de validación cercana a 0.776.
2. **Bosque aleatorio**: se probaron valores de `n_estimators` de 1 a 9. El modelo óptimo usó 9 árboles y alcanzó aproximadamente 0.781 de exactitud en validación.
3. **Regresión logística**: con el solver `liblinear`, obtuvo una exactitud de alrededor de 0.76 en el conjunto de prueba.

El **bosque aleatorio** fue el modelo que superó con más margen el umbral de 0.75 y se recomienda para recomendar el plan adecuado.

## Cómo ejecutar
1. Crear un entorno virtual e instalar las dependencias:
   ```bash
   pip install -r requirements.txt
   ```
2. Abrir el notebook `megaline_parte_2.ipynb` y ejecutar las celdas para reproducir el análisis.

