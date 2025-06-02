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
\
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

## Prácticas recomendadas para las peticiones  
- ***Crear peiciones claras y concisas***: Las peticiones deben de ser **sencillas** y se debe **evitar la ambigüedad**. Las peticiones claras conducen a respuestas más coherentes.

    ``` python

    ## Petición inadecuada
    Calcule la suma total de la siguiente secuencia de números: 4, 8, 12, 16.

    ## Petición adecuada
    ¿Cual es la suma de estos números: 4, 8, 12, 16?

    ```  
- ***Incluya contexto si es necesario***: Proporcione cualquier **contexto adicional** que ayude al modelo a responder con precisión. 
    ``` python

    ## Petición inadecuada
    Resuma este artículo: [Texto]

    ## Petición adecuada
    Proporcione un resumen de este artículo para usarlo en una entrada de blog: [Texto]

    ```  
- ***Use directivas para el tipo adecuado de respuesta***: Se desea un formato de resultado en particular, como un resumen, una pregunta o un poema, **especifique el tipo de respuesta directamente**.
    ``` python

    ## Petición inadecuada
    ¿Cuál es la captial?

    ## Petición adecuada
    ¿Cuál es la captial de Nueva York? Responda con una oración completa

    ```
- ***Tenga en cuenta el resultado en la petición***: **Mencione el resultado solicitado** al final de la petición para mantener el modelo centrado en el contenido adecuado.
    ``` python

    ## Petición inadecuada
    Calcule el área de un círculo

    ## Petición adecuada
    Calcule el área de un círculo con un radio de 7,6cm (3 pulg.). Redondee la respuesta al número entero más cercano

    ```
- ***Inicie las peticiones con preguntas***: Formule su entrada en forma de pregunta y **comience con palabras, como quién, qué, dónde, cuándo, por qué y cómo**.
    ``` python

    ## Petición inadecuada
    Resuma este evento

    ## Petición adecuada
    ¿Por qué ocurrió este evento? Expliqueen tres oraciones

    ```

- ***Proporcione un ejemplo de repsuesta***: Utilice el **formato de resultado esperado como ejemplo** de respuesta en la petición.
``` python

## Petición inadecuado
Determine el sentimiento de esta publicación de redes socales: [Texto]

## Petición adecuada
Determine el sentimiento de la siguiente publicación de redes sociales en función de estos ejemplos:
publicación: “excelente bolígrafo” => Positivo
publicación: “Odio cuando mi teléfono se queda sin batería” => Negativo
[insertar publicación de redes sociales] =>

```  

- ***Divida las tareas complejas***: Los modelos fundacionales puede confundirse cuando se le pide que realicen tareas complejas.
    - Divida la tarea en varias subtareas. Si no puede obtener resultados fiables, intente dividir la tarea en varias peticiones.
    - Pregúntele al modelo si entendió sus instrucciones. Proporcione aclaraciones basadas en la respuesta del modelo.
    - Si no sabe como divir la tarea en subtareas, pídale al modelo que piense paso a paso.

- ***Experimente y use la creatividad***: Pruebe diferente peticiones para optimizar las respuestas del modelo. Determine qué peticiones logran resultados eficaces y cuáles obtienen resultados inexactos.  

- ***ese plantillas de peticiones***: Las plantillas de peticiones son estructuras o formatos predefinido que se pueden usar para proporcionar entradas consistentes a los FM.


## Situación
el siguiente es un ejemplo de analisis y optimización de una petición.
``` python

## Petición original
Genere un informe de análisis de mercado para un nueva categoria de productos.

## Petición actualizada
PARÁMETROS
Temperatura: 0,9
Top-p: 0,999
Longitud Máxima: 5000

PETICIÓN
Genere un informe de análisis de mercado completo para una nueva categoría de productos en la industria financiera para una audiencia de pequeñas y medianas empresas (pymes). Estructure el informe con las siguente secciones.

1. resumen ejecutivo
2. Información general de la industria
3. Análisis del público objetivo
4. Panorama competitivo
5. Oportunidad de producto y recomendaciones
6. Proyecciones financieras

```  
\
Técnicas de ingeniería de peticiones
==  
El uso de estas técnicas de ingeniería de peticiones puede servir de ayudar para **utilizar los modelos generativos de la manera más eficaz** a fin de alcanzar sus objetivos únicos.  

## Peticiones sin entrenamiento previo  
El usuario **presenta una tarea** a un modelo generativo **sin proporcionar ningun ejemplo o entrenamiento** explícito para esa tarea específica. **Los FM modernos han demostrado un impresionante rendimiento en las peticiones sin entramiento previo**.
- Cuanto más grande y capaz sea el FM, mayor será la probabilidad de obtener resultados efectivos con peticiones sin entrenamiento previo.
- El ajuste de las intrucciones, un proceso de ajuste de los modelos para alinearlos mejor con las preferencias humanas, puede mejorar las capacidades de aprendizaje sin entrenamiento previo.  

Ejemplo de petición de entrenamiento previo  
|Petición| Resultado|
|-|-|
|Indique el sentimiento que le genera la siguiente publicación de redes sociales y clasifiquelo cono positivo, negativo o neutro:|**POSITIVO**|  
|¡Un enorme agradecimiento al increible equipo de AnyCompany! Su servicio de atención al cliente de primera categoría sigue dejándome boquiabierto. ¡Es un orgullo ser cliente fiel!|

## Paticiones a partir de algunos ejemplos  
Consiste en **proporcionar un modelo de lenguaje con ejemplos contextuales** para guiar su comprensión y el resultado esperado para una tarea específica.
- Asegúrese de seleccionar ejemplos que sea representativos de la tarea que desea que realice el modelo y que abarquen una amplia gama de entrada y resultados.
- Experimente con la cantidad de ejemplos. La cantidad óptima de ejemplso para incluir en una petición a partir de algunas ejemplos puede variar según la tarea.  

Ejemplo de petición con algunas ejemplos
|Petición|Resultado|
|-|-|
|Indique el sentimiento que le genera el siguiente titular de la noticia y clasifíquelo como positivo, negativo o neutral. Estos son algunos ejemplos:|**POSITIVO**|
|Firma de inversión rechaza las acusaciones de corrupción. **Respuesta: Negativo**||
|Profesor local galardonado con un premio nacional. **Respuesta: Positivo**||
|Organización cominutaria supera la meta de recaudación de fondos destinados a proporcionar comida a miles de personas necesitadas. **Respuesta**|**POSITIVO**  

## Peticiones con cadena de pensamiento  
La técnica de peticiones con cadena de pensamiento ***(Chain-of-thought, CoT)*** **divide las tareas de rezonamiento intrincadas en pasos intermedios más pequeños**.
- ***CoT con peticiones sin entrenamiento previo***:  
    ``` python

    ## PETICION
    Según la siguiente información: ¿Qué servicio requier un depósito mayor?

    - El costo total del servicio A es de 50,000 USD y requiere un depósito del 30%.
    - El costo total del servicio B es de 40,000 USD y requiere un depóstio del 40%.

    Piensa paso a paso.


    ## RESULTADO
    El depósito para el servicio A es el 30% de 50,000 USD, que es 
    0,3 x 50,000 = 15,000 USD

    El depósito para el servicio B es el 40% de 40,000 USD, que es
    0,4 x 40,000 = 16,000 USD

    Por lo tanto según la información proporcionada, el servicio B requier un depósto mayor.

    ```  
- ***CoT con peticiones a partir de algunos ejemplos***:  
    ``` python

    ## PETICION
    Pregunta: Si hay 2 bolsas y cada una tiene 3 naranjas, ¿Cuántas naranjas hay en total?
    Respuesta: 2 bolsas, 3 naranjas en cada una. 2 × 3 = 6 naranjas.

    Pregunta: si hay 4 automóviles y en cada uno hay 2 pasajeros, ¿cuántos pasajeros hay en total?
    Respuesta: 4 automóviles, 2 pasajeros cada uno. 4 × 2 = 8 pasajeros.

    Pregunta: si hay 3 canastas y cada una tiene 5 manzanas, ¿cuántas manzanas hay en total?
    Respuesta: (piense paso a paso)


    ## RESULTADO
    Respuesta: 3 canastas, 5 manzanas en cada una. 3 × 5 = 15 manzanas.

    ```  

## Situación  
Supongamos que tiene una plantilla de informe de análisis de mercado. También tiene algunos informes de análisis de mercado para otros productos nuevos que su organización ha lanzado.
- Petición de la situación actualizada con la técnica de peticiones a partir de algunos ejemplos
    ``` python

    ## PETICIÓN
    Genere un informe de análisis de mercado completo para una nueva categoría de productos en la industria financiera. El público objetivo son la pequeñas y medianas empresas (mypes). Utilice la plantilla para ordenar el informe en categorías. [adjunte la plantilla del informe]

    Los siguiente ejemplos son informes de análisis de mercado para productos lanzados anteriores.

    Ejemplo 1: [inserte un ejemplo de un informe de análisis de mercado]

    Ejemplo 2: [inserte un ejemplo de un informe de análisis de mercado]

    ```