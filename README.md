# Proyecto9_Clustering_Regresion

Con relación a este proyecto, descubri algunos retos iniciales como:
- Tener una poca cantidad de personas (795) pero que estas están presentes en todas las regiones, todos los mercados y en dintintos países.
- Cada persona tiene correspondiente a sí misma, una lista de facturas pero a la vez están desglosadas por cada artículo. De manera que nuestro conjunto de datos en realidad son todas las ordenes de todas las facturas, desagrupadas. Esto a la vez tiene un detalle, que cada persona tiene 2 Customer ID distintos. Por lo que para mí lo más lógico fue agrupar por cliente para tratar de descubrir cluster en base al comportamiento general del cliente.

Para hacer mi clusterizaicón tomé el siguiente abordaje, creando un nuevo data frame con las siguientes columnas:
- facturas_total = conteo general de las ordenes (aún contando que algunas forman parte de las mismas)
- descuento_medio = media del descuento que ha podido utilizar la persona
- compras_total = suma total de las ventas por cliente
- compras_media = media de las ventas por cliente
- beneficio_total = suma de todo el profit de las órdenes del cliente
- costo_envio_medio = media del costo de envío por cliente

Métodos mas semejantes a lo visualizado con los datos: k_means arrojó 2 clusters. Uno de 531 vs 264; el método de Ward con euclidian arrojó 278 vs 517.

El método ard hace una separación más clara entre mis grupos de clientes.