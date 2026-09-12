# Actividad 06 — Algoritmos Genéticos en Machine Learning

## 1. Feature selection

Se utilizó una Regresión Logística en el dataset `breast_cancer`.

El cromosoma tiene 30 genes binarios. Un valor de `1` indica que la característica se utiliza y `0` que se descarta. Se mide con accuracy.

El algoritmo seleccionó 18 de las 30 características. El accuracy pasó de **0.9508 a 0.9543**, por lo que se obtuvo un modelo con menos características y una ligera mejora en la precisión.

## 2. Hyperparameter optimization

Se utilizó un `SVC` en el dataset `digits`.

El cromosoma contiene dos valores reales:

```text
[log10(C), log10(gamma)]
```

Se utiliza una escala logarítmica. La aptitud es el accuracy medio del SVC.


```text
C = 11.305
gamma = 0.00099
accuracy = 0.9761
```

Este resultado superó la búsqueda manual utilizada como referencia.

## 3. Neuroevolution

Se utilizó un `MLPClassifier` sobre el dataset `digits`.

El cromosoma representa la arquitectura de la red y la tasa de aprendizaje:

```text
[neuronas capa 1, neuronas capa 2, log10(tasa de aprendizaje)]
```

El valor `0` en la segunda capa indica que la red utiliza una sola capa oculta.

El algoritmo encontró una arquitectura **MLP(65, 43)** con una tasa de aprendizaje aproximada de **0.0067**, alcanzando un accuracy de **0.9232**.

## Ciclo del AG

- Representación: Cromosomas binarios, reales o mixtos según el problema
- Inicio: Población aleatoria con `np.random.default_rng(seed)`
- Validación: Accuracy medio
- Selección: Mediante Torneo
- Fin: Máximo de generaciones, conservando el mejor individuo

## Conclusiones

- Los algoritmos genéticos permiten buscar soluciones sin utilizar gradientes.
- En los tres experimentos se utilizó el mismo motor genético. Lo que cambia es la
forma de representar una solución. 
- Se conserva al mejor de cada generación
