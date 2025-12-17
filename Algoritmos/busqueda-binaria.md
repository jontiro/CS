# Búsqueda Binaria

## Descripción

La búsqueda binaria es un algoritmo eficiente para encontrar un elemento en una lista ordenada. Funciona dividiendo repetidamente a la mitad la porción de la lista que podría contener el elemento, hasta reducir las ubicaciones posibles a solo una.

## Complejidad

- **Temporal**: O(log n)
- **Espacial**: O(1) - versión iterativa, O(log n) - versión recursiva

## Requisitos

- La lista debe estar ordenada

## Implementación en Python

```python
def busqueda_binaria(arr, objetivo):
    """
    Busca un elemento en un array ordenado
    
    Args:
        arr: Lista ordenada de elementos
        objetivo: Elemento a buscar
    
    Returns:
        Índice del elemento si se encuentra, -1 en caso contrario
    """
    izquierda = 0
    derecha = len(arr) - 1
    
    while izquierda <= derecha:
        medio = (izquierda + derecha) // 2
        
        if arr[medio] == objetivo:
            return medio
        elif arr[medio] < objetivo:
            izquierda = medio + 1
        else:
            derecha = medio - 1
    
    return -1

# Ejemplo de uso
numeros = [1, 3, 5, 7, 9, 11, 13, 15]
resultado = busqueda_binaria(numeros, 7)
print(f"Elemento encontrado en el índice: {resultado}")  # Output: Elemento encontrado en el índice: 3
```

## Casos de Uso

- Búsqueda en diccionarios
- Bases de datos indexadas
- Búsqueda en arrays ordenados grandes
- Algoritmos de optimización

## Ventajas

- Muy eficiente para conjuntos de datos grandes
- Complejidad logarítmica
- Implementación sencilla

## Desventajas

- Requiere que los datos estén ordenados
- No es eficiente para conjuntos pequeños de datos
