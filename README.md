# Proyecto9_Clustering_Regresion

Con relación a este proyecto, descubri algunos retos iniciales como:
- Tener una poca cantidad de personas (795) pero que estas están presentes en todas las regiones, todos los mercados y en dintintos países.
- Cada persona tiene correspondiente a sí misma, una lista de facturas pero a la vez están desglosadas por cada artículo. De manera que nuestro conjunto de datos en realidad son todas las ordenes de todas las facturas, desagrupadas. Esto a la vez tiene un detalle, que cada persona tiene 2 Customer ID distintos. Por lo que para mí lo más lógico fue agrupar por cliente para tratar de descubrir cluster en base al comportamiento general del cliente.

Para hacer mi clusterización tomé el siguiente abordaje, agrupé las variables numéricas de la siguiente forma para poder abordar el problema creando un nuevo data frame con las siguientes columnas:
- facturas_total = conteo general de las ordenes (aún contando que algunas forman parte de las mismas)
- descuento_medio = media del descuento que ha podido utilizar la persona
- compras_total = suma total de las ventas por cliente
- compras_media = media de las ventas por cliente
- beneficio_total = suma de todo el profit de las órdenes del cliente
- costo_envio_medio = media del costo de envío por cliente

Métodos mas semejantes a lo visualizado con los datos: k_means arrojó 2 clusters. Uno de 531 vs 264; el método de Ward con euclidian arrojó 278 vs 517. El método ward hace una separación más clara entre mis grupos de clientes. Esta separación estuvo marcada por los clientes que consumen más por encima de aquellos que consumen menos. En resumen, el grupo con menor cantidad es el que más gastos tiene en Sales al igual que en casi todas las otras variables numéricas. 

Modelos:

En mi primer modelo, 
    - para el Cluster_0: con solo una variable numérica obtuve resultados con underfitting. Esto me arroja que debo brindarle más datos a mi modelo para que pueda aprender mejor y no sea tan generalizado. La mejor opción resultó Gradient Boosting.
    - para el Cluster_1: se sigue apreciando underfitting, para este cluster el mejor modelo se encontró gracias al Random Forest.
    
En el segundo modelo, di entrada a otras 2 nuevas columnas demográficas, para que pueda obtener más información de mis datos. Esto no mejoró las métricas del modelo enormemente las métricas.
    - para el Cluster_0: 

En el tercer modelo, mantengo las 2 nuevas columnas demográficas (Region y Country), para que pueda obtener más información de mis datos. Además, dejé la variables Quantity como numérica. En este caso, viendo la interacción de Sales con Shipping Cost, quité una serie de outliers. Con todo esto, mis métricas mejoraron su error (r2) aunque los valores de RMSE son algo elevados.