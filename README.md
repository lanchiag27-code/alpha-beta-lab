
# Laboratorio: Minimax y Poda Alfa-Beta

## Descripción

Este proyecto implementa los algoritmos Minimax y Poda Alfa-Beta para resolver un árbol de decisión simplificado.

Minimax analiza las alternativas disponibles para encontrar la mejor decisión, mientras que Poda Alfa-Beta optimiza la búsqueda descartando ramas que no pueden mejorar el resultado final.

## Objetivo

Comparar el resultado y la eficiencia de Minimax frente a Poda Alfa-Beta, considerando la cantidad de nodos evaluados y las ramas podadas.

## Instalación

Crear el entorno virtual:

```bash
python -m venv .venv
```

Activar el entorno virtual en Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

Instalar las dependencias:

```bash
pip install -r requirements.txt
```

## Ejecución

```bash
python -m src.main
```

## Pruebas unitarias

```bash
python -m pytest
```

Ejecutar pruebas con cobertura:

```bash
python -m pytest --cov=src --cov-report=term-missing --cov-report=xml
```

## Resultados obtenidos

| Árbol | Minimax | Alfa-Beta | Nodos Minimax | Nodos Alfa-Beta |
|---|---|---|---|---|
| Sample Tree | 3 | 3 | 4 | 3 |
| Medium Tree | 7 | 7 | 12 | 8 |
| Ordered Tree | 8 | 8 | 12 | 8 |

Los resultados muestran que ambos algoritmos obtienen el mismo valor de decisión. Sin embargo, Poda Alfa-Beta permite reducir la cantidad de nodos evaluados.

## Preguntas de análisis

### 1. ¿Por qué Alfa-Beta obtiene el mismo resultado que Minimax si no evalúa todo el árbol?

Porque Alfa-Beta descarta únicamente las ramas que no pueden mejorar la decisión final. Por eso mantiene el mismo resultado que Minimax, pero realiza menos evaluaciones.

### 2. ¿Qué representa alpha dentro del algoritmo?

Alpha representa el mejor valor que el jugador MAX puede garantizar hasta el momento durante la búsqueda.

### 3. ¿Qué representa beta dentro del algoritmo?

Beta representa el mejor valor que el jugador MIN puede garantizar hasta el momento durante la búsqueda.

### 4. ¿En qué casos la Poda Alfa-Beta ahorra más trabajo?

Cuando las mejores opciones se exploran primero, permitiendo descartar rápidamente las ramas que no pueden mejorar el resultado.

### 5. ¿Por qué el orden de exploración afecta el rendimiento?

Porque explorar primero los movimientos más favorables permite actualizar antes los valores alpha y beta, facilitando la poda de ramas innecesarias.

### 6. ¿Qué pasaría si el rival no juega de manera racional?

El algoritmo podría tomar decisiones demasiado conservadoras, ya que Minimax supone que el adversario siempre selecciona la mejor jugada posible.

### 7. ¿Cómo se relaciona este algoritmo con motores de ajedrez?

Los motores de ajedrez pueden utilizar búsqueda Minimax con Poda Alfa-Beta para analizar movimientos y descartar alternativas que no mejoran la posición evaluada.

### 8. ¿Qué limitaciones tiene este enfoque frente a redes neuronales o aprendizaje por refuerzo?

Minimax y Alfa-Beta necesitan representar estados, movimientos y funciones de evaluación. En juegos complejos, el árbol puede crecer demasiado. Las redes neuronales y el aprendizaje por refuerzo pueden aprender estrategias a partir de datos o experiencias, aunque también requieren recursos y entrenamiento.

## Conclusión

El laboratorio permitió implementar y comparar dos algoritmos de búsqueda adversarial. Se comprobó que Minimax y Poda Alfa-Beta generan el mismo valor de decisión, pero Alfa-Beta puede reducir la cantidad de nodos evaluados, mejorando la eficiencia del proceso de búsqueda.
