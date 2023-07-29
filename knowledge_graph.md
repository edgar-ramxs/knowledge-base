# Explore Grocery Transactions using a Knowledge Graph 
*Titutlo: Explore las transacciones de comestibles usando un grafico de conocimiento.*

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

"Una guía de copiar y pegar para generar un gráfico de conocimiento con bibliotecas de python spacy, textacy y netwkorx. El siguiente ejemplo procesa solo una oración como texto sin formato. puede reemplazarlo con el texto que desee". [Enlace](https://alfarruggia.medium.com/how-to-generate-a-knowledge-graph-from-plain-text-in-few-steps-42f3a639155f)





# Building a Knowledge Base from Texts: a Full Practical Example
*Titulo: Construcción de una base de conocimientos a partir de textos: un ejemplo práctico completo*

¡Hola, compañeros entusiastas de la PNL! En este artículo, vemos cómo implementar una canalización para extraer una base de conocimiento de textos o artículos en línea. Hablaremos sobre el reconocimiento de entidades con nombre, la extracción de relaciones, la vinculación de entidades y otros pasos comunes que se realizan al crear gráficos de conocimiento. Puede probar la demostración final en este Hugging Face Space y verificar el código en Colab.



