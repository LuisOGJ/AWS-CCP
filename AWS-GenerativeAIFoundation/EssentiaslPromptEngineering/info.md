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

Modificación de Peticiones
==  
Técnicas para modificar y refinar peticiones a fin de lograr mejores resultados.  
- Modelos fundacionales (FM)

## Parámetros de inferencia
Al interactuar con FM, es posible configurar parámetros de inferencia para limitar o influir en la respuesta del modelo. Los **parámetros pueden variar según el modelo** en uso. Los parámetros de inferencia se ajustan a una variedad de categorías. Las más comunes son; **la aleatoriedad, la diversidad y la longitud**.  


### Aleatoriedad y diversidad
Esta es la categoría más común de parámetros de inferencia. Influyen en la variación de las respuestas generadas, ya que **limintan los recursos a los más probables o cambian la forma de la distribución de probabilidad de los resultados**. Tres de los parámetros **más comunes son la temperatura, el top-k y el top-p**.  
- ***Temperatura***: Este parámetros controla la **aleatoriedad o la creatividad** del resultado del modelo. Una **tempratura más alta hace que el resultado sea más diverso o impredecible**. La temperatura se estable entre 0 y 1. 

    |Temperatura baja (0,2)| Temperatura alta (1,0)|
    |-|-|
    |Los resultados son más conservadores, repetiticos y se centran en las respuestas más probables.|Los resultados son más diversos e impredecibles, pero pueden ser menos coherentes o relevantes.|

- ***Top-p***: Es una configuración que **controla la diversidad del texto**, ya que **limita la cantidad de palabras entre las que el modelo puede elegir** en función a sus probabilidades. Top-p también se establece en una escala del 0 al 1.

    |Top-p bajo (0,250)|Top-p alto (0,990)|
    |-|-|
    |El modelo **solo considerará palabras que contituyan el 25% más probable** de la distribución total de probabilidad. Esto puede **ayudar a que el resultado sea más centrado y coherente**, porque el modelo se limita a elegiar entre las **palabras más probables** según el texto.|El modelo **considerará una amplia gama de palabras posibles para la siguiente palabra** de la secuencia, ya que **incluirá palabras que contituyan al 99% más probable** de la distribución total de probabilidad. Esto puede hacer que el resultado sea más diverso y creativo, porque el modelo **tiene un conjunto más amplio de palabras para elegir**.|

- ***Top-k***: **Limita la cantidad de palabras a la cantidad de palabras de top-p más probables**, independientemente de sus probabilidades porcentuales. Por ejemplo, **si top-k se establece en 50, el modelo solo considerará 50 palabras más probables para la siguiente palabra** de la secuencia, incluso si esas 50 palabras solo constituyen una pequeña parte de la distribución total de probabilidad.

    |Top-k bajo (10)|Top-k (500)|
    |-|-|
    |El modelo solo **considerará las 10 palabras más probables para la siguiente palabra de la secuencia**. Esto puede ayudar a que el **resultado sea más centrado y coherente**, porque le modelo se limita a elegir **las palabras más probables según el contexto**|El modelo considerará las **500 palabras más probables para la siguiente palabra de la secuencia**, **independiente de sus proabilidades individuales**. Esto puede hacer que el **resultado sea más diverso y creativo**, porque le modelo tieneun conjunto más amplio de palabras posibles entre las que elegir.|

### Longitud  
Se refiere a la **configuración que controlan la longitud máxima del resultado generado** y especifican las **secuencias de detención que indican el final del proceso de generación**.

- ***Longitud máxima***: Determina la **cantidad máxima de tokens que el modelo puede generar** durenta el proceso de inferencia. Ayuda a **evitar que el modelo genere resultados excesivos o infinitos**, lo que podría provocar el agotamiento de los recursos o un comportamiento no deseado. El valor adecuado para esta configuración depende de la tarea específica y de la longitud de resultado deseada. Por ejemplo, en las tareas de generación de lenguaje natural, **como el resumen o la traducción de textos, la longitud máxima se puede establecer en función de la longitud típica del texto de destino**. En las tareas de generación abiertas, como la **escritura creativa o los sistemas de diálogo, podría ser conveniente una longitud máxima más alta para permite resultados más extensos**.  

- ***Secuencias de detención***: Las secuencias de detención son **tokens especiales o secuencias de tokens que le indican al modelo que deje de generar más resultados**. Cuando el modelo encuentra una secuencia de detención durante el proceso de inferencia, temrinará la generación. **Independientemente de la configuración de longitud máxima**. Las secuencias de detención **son particularmente útiles en tareas en las que la longitud del resultado deseado es variable o difícil de predecir** con anticipación. Por ejemplo, en los sistemas de **IA conversacional, la secuenca de detención podría ser un token de final de conversación o una frase específica** que indique el final de la respuesta.

La secuencias de detención **puede predefinirse o generarse dinámcamente en función de la entrada o del propio resultado generado**. En algunos casos, se pueden **especificar múltiples secuencias de detención**. Esto le permite al modelo detener la generación cuando encuentre cualquiera de las secuencias definidas.