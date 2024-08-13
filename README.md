
HENRY </p>
Proyecto Individual 2 </p>
Dashboard Telecomunicaciones
=======

Henry DataPT9 
</p>
Maria Isabel Arango ☑️ 
</p>

## Introducción:

En este segundo proyecto tomo el roll de **`Data Analist`** en una empresa prestadora de servicios de telecomunicaciones, especialmente el de brindar acceso a internet. 
El objetivo del proyecto es realizar un análisis del sector de telecomunicaciones con el fin de dar a la empresa un marco de información que le permita identificar oportunidades de crecimiento.

A continuación se explica el paso a paso del desarrollo de este proyecto.

## Desarrollo:
</p>
Para la realización del proyecto se siguieron los siguientes pasos:
</p>

**0. Preparación de los Archivos Fuente de Información:**
La información fuente es suministrada en el archivo de Excel  **`Internet.xlsx`** el cual contiene 15 hojas con información. Con el fin de poder acceder a ella se realiza una programación VBA (Visual Basic for Applications) en Excel la cual convierte cada una de las hojas en un archivo en formato CSV. (Ver archivo **`Internet-Trabajado.xlsm`** :eyes: ). 
</p>
Como resultado se obtienen los siguientes Archivos (Disponibles en la carpeta /Data CSV):
</p>

- Acc_vel_loc_sinrangos.csv
- Velocidad_sin_Rangos.csv
- Velocidad % por prov.csv
- Totales VMD.csv
- Accesos_tecnologia_localidad.csv
- Totales Accesos Por Tecnología.csv'
- Accesos Por Tecnología.csv
- Data CSV/Totales Dial-BAf.csv
- Penetración-poblacion.csv
- Penetracion-hogares.csv
- Penetracion-totales.csv
- Totales Accesos por velocidad.csv
- Accesos por velocidad.csv
- Ingresos.csv
  
</p>

**1. Limpieza de Datos:** </p>
   En este paso se realiza el cargue y un análisis inicial de datos con el fin de limpiarlos y prepararlos para su uso. (Ver archivo **`Análisis de Datos.ipyn`** :eyes: ).
   </p>
   En el notebook se carga la información del sector ya en formato CSV obteniendo los siguientes datasets:  </p>
   
- data_acc_vel_loc_sinr
- data_Vel_sin_r 
- data_vel_prc_prov
- data_total_VMD 
- data_acc_tec_loc
- data_total_acc_por_tec 
- data_acc_por_tecn 
- data_dial_BAf 
- data_total_Dial_BAf 
- data_pen_poblacion 
- data_pen_hogares 
- data_pen_total 
- data_total_acc_por_vel 
- data_acc_por_vel 
- data_ingresos 
</p>
Una vez cargados los archivos como dataframe, se procede a visualizar la información para posteriormente limpiarla. 
</p>

Para cada Dataframe se realiza los siguiente:
</p>
1. Ver información del número de filas y columnas, tipos de datos, nostrar los primeros registros de las tablas, nombres de las columnas y verificación de las filas duplicadas (de haberlas se eliminan).  ➡️ Función visualiza()
2. Reemplazar valores nulos de columnas numericas por zero. ➡️ Función nulos_por_ceros()
3. Limpia las columnas de texto correspondientes a variables categóricas eliminando espacios en blanco sobrantes y se convierte el texto a formato título. Los caracteres especiales como "*" se limpian según sea el caso. ➡️ Función limpia_texto()
4. Se cambian los nombres de las columnas eliminando espacios en blanco al principio y final, y separando palabras con _. ➡️ Función formatear_nombre_columnas()
5. Se verifica que las columnas con información numerica cómo número de Accesos, estén en formato número, de no ser asi, se les cambia el type.  ➡️ Función de_object_a_numerica()
6. Algunas tablas están un formato horizontal por lo que requieren ser transpuestas para lograr un mejor manejo y análisis de la data.
7. A las tablas con columnas de Año y Trimestre se les agrega una columna "Fecha" en formato datetime concatenando los datos de año y trimestre.
8. Se analizan y eliminan los outliets. Primero se presentan visualmente en un grafico de cajas y bigotes, y luego se analizan numericamente con la metodología de z-score. ➡️ Funciones grafico_outliers() , detectar_outliers() , eliminar_outliets()
9. Se hace un describe para ver la información de estadísitica básica de las variables numéricas.
10. En algunas tablas se requieren transformaciones especificos a los datos y se realzian según sea en caso.

Finalmente, los archivos limpios y listos para ser utilizados en el dashboard son exportados en formato CSV en la carpeta /Data fuente Dashboard

Nota:  👁️ Con el fin de Agilizar el proceso de Limpieza se crean las funciones.


</p>

**2. Análisis de Datos (EDA):**
</p>

Para cada dataset se realiza un análisis gráfico. Los graficos se seleccionan de acuerdo con los datos a analizar. 
Por ejemplo, para el dataset  **`data_Vel__sin_r`** que presenta la información sobre la velocidad de conexión a internet sin rangos específicos, se realizan las siguientes graficas:

La Variable numerica número de conexiones se grafica año a año con el fin de ver su tendencia en el tiempo. En la siguiente grafica se observa como la tendencia es decreciente.

<img src ="/Imagenes/Grafica Ejemplo 1.png">

</p>
Se incluye tambien el detalle del número de conexiones por provincia, en este caso se filtran el paretto (20% de las provincias que generan el 80% de las conexiones):

<img src ="/Imagenes/Grafica Ejemplo 2.png">

👀 El detalle del análisis de cada dataset se puede ver en el notebook de python : **`Análisis de Datos.ipyn`** 
👀 Las conclusiones del análisis se pueden ver en el apartado ANALISIS DE RESULTADOS Y CONCLUSIONES de este documento.


**3. Generación del DashBoard:**

El Dashboard se generó en la herramienta :atom: PowerBI :atom:. 
Inicialmente se suben los archivos fuente con PowerQuery, donde se hace un ajuste en el formato de los datos. 
Se crean las relaciones entre tablas y la tabla calendario (jerarquia de fechas), dejandolos listos para ser modelados.
 
<img src ="/Imagenes/Grafica 3.png">

## ANALISIS DE RESULTADOS Y CONCLUSIONES: 
   </p>
