# Explore Grocery Transactions using a Knowledge Graph 
*Titutlo: Explore las transacciones de comestibles usando un grafico de conocimiento.* 
[Código](./src/multi-graph.py)

 "Cómo crear un gráfico de conocimiento a partir del conocido Groceries Dataset y explorarlo para obtener información. El código está en el lenguaje de programación python y explota las bibliotecas pandas y netwkorx". 
 [Enlace](https://alfarruggia.medium.com/explore-grocery-transactions-using-a-knowledge-graph-db04bf013dde)

Este articulo describe una investigacion de como se puede recolectar informacion relacionada representada en un multigrafo con el datase [Groceries Dataset](https://www.kaggle.com/datasets/heeraldedhia/groceries-dataset)

El dataset contiente datos basados en las ventas de un almacen donde se registra: el miembro que hizo la compra, la fecha que se relizo la compra y, el producto que se compro. 

En este ejemplo, se hizo creo un dato en base a la compra de cierto miembro en cualquier fecha, esto se nombró como un comprobante con esta estructura "_Member_number_Date_".  

Para la contruccion del grafico, se clasifican los nodos del grafo segun: productos, miembros y recibos. Estas son las tres especies de nodos que se relacionan dentro de este multigrafo. 

Dentro del grafo, los nodos tendran ciertas tipos de conexiones que representan los hechos de la vida real.
+ Un miembro tiene un o más recibos. Esta relacion se denomina _has_purchased_.
+ Un recibo tiene uno o más productos. Esta relacion se denomina _has_item_. 

Para este ejemplo, se reune estos conjuntos de relaciones en una tupla la cuales son a su vez son listas de la representacion de las relaciones entre nodos. 

"Podemos ver, por ejemplo, que el usuario 1808 tuvo la compra 21–07–2015 comprando leche entera."

Con esto, este ejercicio quiere recuperar informacion con respecto a la venta de productos del almacen. Se quiere crear una promocion para un producto en stock de poca ventas pueda ser vendido conjunto a otros. Para ello, elarticulo recolecta los 10 productos mas vendidos y los 10 menos vendidos, segun la cantidad de relaciones que tengan los nodos de los productos. Luego de ello, seguiran estos pasos:

1) Seleccionar un producto menos importante para hacer la promocion
2) Encontrar los recibos conectados al producto 
3) Encontrar la conexion del producto menos importante con el mas importante que se tenga registro en los recibos.

Con esto se puede realizar un analisis y crear una promocion para vender el producto menos vendido con otros. 



# How to generate a Knowledge Graph from plain text in few steps
*Titulo: Cómo generar un gráfico de conocimiento a partir de texto sin formato en pocos pasos.*
[Código](./src/graph_from_plain_text.py)

"Una guía de copiar y pegar para generar un gráfico de conocimiento con bibliotecas de python spacy, textacy y netwkorx. El siguiente ejemplo procesa solo una oración como texto sin formato. puede reemplazarlo con el texto que desee". [Enlace](https://alfarruggia.medium.com/how-to-generate-a-knowledge-graph-from-plain-text-in-few-steps-42f3a639155f)

En este proyecto, se enfoca en la extracicon partes en base de SVO, sujeto-verbo-objeto. SVO es un término que se utiliza en la tipología lingüística para designar un tipo determinado de lengua teniendo en cuenta la secuencia no marcada o neutra de una lengua.

Tiende a ser el orden predeterminado porque el verbo se usa para dividir el sujeto del predicado, sin necesidad de usar partículas para indicar dónde empieza o termina un sujeto o predicado. Es, por ende, una de las secuencias más frecuente, y de hecho es usada en la mayoría de lenguas occidentales y un buen número de orientales. 

El chino mandarín, el español y el inglés, algunos de los idiomas más hablados del mundo, presentan dicho orden gramatical.

En el grafo, se extraen los Sujetos y Objetos para representarlos como nodos, ademas, se extraen las relaciones entre estos y se etiquetan como "acción". 




# Building a Knowledge Base from Texts: a Full Practical Example
*Titulo: Construcción de una base de conocimientos a partir de textos: un ejemplo práctico completo* [Enlace](https://medium.com/nlplanet/building-a-knowledge-base-from-texts-a-full-practical-example-8dbbffb912fa)

*¡Hola, compañeros entusiastas de la PNL! En este artículo, vemos cómo implementar una canalización para extraer una base de conocimiento de textos o artículos en línea. Hablaremos sobre el reconocimiento de entidades con nombre, la extracción de relaciones, la vinculación de entidades y otros pasos comunes que se realizan al crear gráficos de conocimiento. Puede probar la demostración final en este Hugging Face Space y verificar el código en Colab.*

Dentro del proyecto, se utiliza el modelo [REBEL](https://github.com/Babelscape/rebel/blob/main/docs/EMNLP_2021_REBEL__Camera_Ready_.pdf). Es un modelo de extraccion de relaciones por generacion de lenguaje de extremo a extremo.

Tambien, en el proyecto se despliega en una interfaz interactiva con Streamlit y es implementada en Hugging Face Spaces. 



## Bases de conocimiento y gráficos de conocimiento. 
> Una [base de conocimiento (KB)](https://en.wikipedia.org/wiki/Knowledge_base) es información almacenada como datos estructurados, lista para usarse para análisis o inferencia. Por lo general, una KB se almacena como un gráfico (es decir, un [gráfico de conocimiento](https://www.ibm.com/topics/knowledge-graph)), donde los nodos son entidades y los bordes son relaciones entre entidades.

> Por ejemplo, del texto “Fabio vive en Italia” podemos extraer la relación tripleta <Fabio, lives in, Italy>, donde “Fabio” e “Italia” son entidades.

> La extracción de trillizos de relaciones del texto sin procesar es una tarea crucial en la extracción de información , que permite múltiples aplicaciones, como completar o validar bases de conocimiento, verificación de hechos y otras tareas posteriores.

Para construir un grafo de conocimiento:
+ Extraer las entidades [Reconocimineto de entidades con nombre (NER)](https://en.wikipedia.org/wiki/Named-entity_recognition). 
+ Extraer las realciones entre entidades [Clasificacion de relaciones (RC)](https://paperswithcode.com/task/relation-classification). 

> REBEL es un modelo de texto a texto entrenado por BabelScape ajustando BART para traducir una oración de entrada sin procesar que contiene entidades y relaciones implícitas en un conjunto de tripletes que se refieren explícitamente a esas relaciones. Ha sido entrenado en más de 200 tipos de relaciones diferentes.

> Los autores crearon un conjunto de datos personalizado para el entrenamiento previo de REBEL, usando entidades y relaciones que se encuentran en los resúmenes de Wikipedia y Wikidata , y filtrándolas usando un modelo de inferencia de lenguaje natural RoBERTa (similar a este modelo ). Eche un vistazo al documento para obtener más información sobre el proceso de creación del conjunto de datos.

## Implementación del grafo de conocimiento
1) Cargue el modelo REBEL de Extracción de Relación.
2) Extraer una base de conocimientos de un texto breve.
3) Extraer una base de conocimiento de un texto extenso.
4) Filtrar y normalizar entidades.
5) Extraiga una base de conocimiento de un artículo en una URL específica.
6) Extraiga una base de conocimiento de varias URL.
7) Visualizar bases de conocimiento.


Necesitamos cada biblioteca por las siguientes razones:

+ transformers : Carga el modo REBEL.
+ wikipedia : valide las entidades extraídas comprobando si tienen una página de Wikipedia correspondiente.
+ newspaper : analizar artículos de URL.
+ GoogleNews : Lea los últimos artículos de Google News sobre un tema.
+ pyvis : visualizaciones de gráficos.

Con la biblioteca *Transformers* pueden cargar un tokenizador y el modelo REBEL previamente entrenado. Para luego, crear un funcion que modifique las cadenas creadas por REBEL para convertirlas en triples de sujetos, objetos y accion. 

Esto genera una lista de relaciones las cuales tiene como elementos diccionarios cuales cuantan con estos atributos:
+ head: El sujeto de la relacion
+ type: tipo de relacion
+ tail: objeto de la relacion

Sin embargo, la tokenizacion de grandes entradas es menos eficiente, por lo que, se decide dividir la tokenizacion en tramos con limites espeficicos en al mismo tiempo relacionarlo con otros tramos. 

>Por ejemplo, podemos dividir un texto de entrada de 1000 tokens largos en ocho tramos superpuestos más cortos de 128 tokens largos y extraer relaciones de cada tramo. Al hacerlo, también agregamos algunos metadatos a las relaciones extraídas que contienen sus límites de tramo. Con esta información, podemos ver de qué parte del texto extrajimos una relación específica que ahora está guardada en nuestra base de conocimiento.

Por lo tanto, la lista de relaciones quedaria asi:
+ head: sujeto
+ type: tipo de relacion
+ tail: objeto
+ meta: un diccionario que contiene metainformación sobre la relación. Este diccionario tiene una spansclave, cuyo valor es la lista de límites de intervalo (por ejemplo, [[0, 128], [119, 247]] ) donde se ha encontrado la relación.

Luego de extraer las primeras relaciones, existe el problema de relacionar demonimaciones semejantes como "Napoleon Bonaparte" y "Napoleon", externamente se sabe que es la misma persona a la cual se hace referencia pero, para el modelo se utiliza un metodo llamado *Entity Linking*, asi se asugura que el modelo se refiere a Napoleon verificando su cuenta de Wikipedia para saber si tiene o no por ese nombre. 



# File GPT, conversación por chat con un archivo
Contexto: 
> FileGPT nació como proyecto dentro de BoxMagic para analizar archivos y datos internos. Con esta herramienta es posible subir archivos de tipo PDF, docx, txt y csv (pronto más tipos de archivo) para entregarle el contexto a OpenAI y comenzar una conversación en base a ese archivo.
[Enlace](https://medium.com/latinxinai/file-gpt-conversaci%C3%B3n-por-chat-con-un-archivo-698d17570358)

Este proyecto, crea un chatbot que analiza los pdf para extraer informacion en forma de pregunta, siguiendo el bot un proceso de extracion de relaciones entre entidades recolectadas del archivo. [Código](./src/file-gpt/app.py)

