Plantilla Postwork Sesion 06
(1) Base de Datos
Aquí pongan el nombre de su base de datos y la o las colecciones que crearon.

Base de datos: Postwork_Proyecto_MALR
Colección:     edificios-que-participan-en-el-macrosimulacro-19s-2019

(2) Consultas
Aquí pongan las consultas que pensaron y como primera línea pongan con qué la van a ejecutar, es decir, un filtro, proyección, ordenamiento, etc.

Las consultas deben usar filtros, proyecciones, expresiones regulares o agregaciones

1. ¿cuántos estados participaron?
Solución:
Agregaciones
Primera etapa por $Group
{
  _id: "$estado",
  estados: {
    $sum: 1
  }
}
solo se ve fueron 35,861 registros de la CIUDAD DE MEXICO y 4 nulos

2. ¿cuántos y cuales municipios participaron?
Primera etapa por $Group
{
  _id: "$municipio",
  municipios: {
    $sum: 1
  }
}
Segunda etapa por $Sort
{
  municipios: 1
}
El resultado lo salvé en una vista denominada municipios_participantes

3. ¿cuántas personas participaron por edificio?
Primera etapa por $Group
{
  _id: "$participantes",      
  tot_participantes: {
    $sum: 1
  }
}
El resultado lo salvé en una vista denominada tot_participante

sin embargo se desplegaron resultados extraños, que necesitamos revisar si se subieron bien los datos o así vienen de origen


Preguntas que no pude aplicar o contestar ahora:

¿Cuál es la lista de todos los documentos que incluyan el "texto" en algún campo?

¿Cuál es el promedio de todos los valores de algún campo como edad, precio, cantidad?
¿Cuál es la cantidad de documentos por tipo de producto o por cierta fecha?
¿Cuál es el producto con más o menos ventas?
¿Cuál es el promedio de ventas en el periodo de cierto año?









