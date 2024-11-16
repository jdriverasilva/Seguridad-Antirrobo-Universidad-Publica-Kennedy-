# Normalizacion

Es un proceso sistemático utilizado en base de datos relacionales para organizar los datos en tablas para eliminar redundancias y garantizar la integridad. Esta implica en 
dividir una tabla cruda en varias tablas relacionadas ,más pequeñas, con datos independientes y que muestren un propósito claro. El proceso consiste en aplicar 
reglas conocidas como formas normales (1FN, 2FN, 3F). Esto mejora la eficiencia, reduce errores y facilita el mantenimiento de la base de datos.


## las tablas iniciales son las siguientes:

<div align="center">
  <img src="./images/cruda1.png" width="80%">
</div>

<div align="center">
  <img src="./images/cruda2.png" width="80%">
</div>

<div align="center">
  <img src="./images/cruda3.png" width="80%">
</div>



## La Primera Forma Normal (1FN):

Es una regla fundamental en el diseño de bases de datos relacionales que establece los siguientes requisitos:

1. Eliminar grupos repetitivos o columnas duplicadas.
2. Crear una tabla separada para cada grupo de datos relacionados.
3. Identificar cada registro con una clave primaria única.
4. Los valores en las columnas deben ser atómicos (indivisibles).

## tabla Usuario

<div align="center">
  <img src="./images/fn1.png" width="80%">
</div>


## Segunda Forma Normal (2NF):

1. Primero debe estar en 1NF (tener una clave primaria y valores atómicos).
2. No debe tener dependencias parciales.

## Tercera Forma Normal (3NF):

1. Debe estar en 2NF.
2. No debe tener dependencias transitivas.
