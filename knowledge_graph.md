[Enlace](https://alfarruggia.medium.com/explore-grocery-transactions-using-a-knowledge-graph-db04bf013dde)
# Explore las transacciones de comestibles usando un grafico de conocimiento
# By Alfonso Farruggia


## Resumen del aritucolo
_Cómo crear un gráfico de conocimiento a partir del conocido Groceries Dataset y explorarlo para obtener información. El código está en el lenguaje de programación python y explota las bibliotecas pandas y netwkorx._

Este articulo describe una investigacion de como se puede recolectar informacion relacionada representada en un multigrafo con el dataset "Groceries Dataset", [Dataset](kaggle.com)

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





