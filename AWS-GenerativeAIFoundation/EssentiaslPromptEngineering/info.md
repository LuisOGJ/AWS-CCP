Comprensión de las peticiones
==  
Cuando interactúa con un modelo de mediante una serie de preguntas, enunciados o instrucciones, puede ajustar el comportamiento de los resultados del modelo en función del contexto específico del resultado que desea lograr.

El uso de estrategias de peticiones puede ayudar:
- Mejorar las capacidades del modelo y reforzar sus medidas de seguridad.
- Equipar el modelo con conocimiento específico del dominio y herramientas externas sin modificar sus parámetros ni realizar ajustes.
- Interactuar con los modelos de lenguaje para comprender su potencial por completo.
- Proporcionar entradas de mayor calidad para obtener resultados de mayor calidad.

## Elementos de una petición
- Instrucciones: Tarea que debe realizar el modelo. Proporciona una descripción de la tarea o una instruccuón sobre cómo debe funcionar el modelo.
- Contexto: Información externa que sirve de guia al modelo.
- Datos de entrada: Entrada para la que se desea una respuesta.
- Indicador de resultado: Tipo o el formato del resultado.  
  
```python

#Intrucciones
Con una lista de los pedidos de los clientes y el inventario disponible, determinar qué pedidos se pueden gestionar y qué artículos se debe reabastecer.

#Contexto
Esta tarea es esencial para la administración de inventarios y los procesos de cumplimientos de pedidos en las empresas minoritarias o de comercio electrónico.

# Datos de entrada
Pedidos: 
- Pedido 1: Producto A (5 unidades), Producto B (3 unidades)
- Pedido 2: Producto A (2 unidades), Producto B (2 unidades)

Inventario: 
- Producto A: 8 unidades
- Producto B: 4 unidades
- Producto C: 1 unidad

# Indicador de resultado
Estado de cumplimiento: 

```

