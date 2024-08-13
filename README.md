
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
</p>
2. Reemplazar valores nulos de columnas numericas por zero. ➡️ Función nulos_por_ceros()
</p>
3. Limpia las columnas de texto correspondientes a variables categóricas eliminando espacios en blanco sobrantes y se convierte el texto a formato título. Los caracteres especiales como "*" se limpian según sea el caso. ➡️ Función limpia_texto()
</p>
4. Se cambian los nombres de las columnas eliminando espacios en blanco al principio y final, y separando palabras con _. ➡️ Función formatear_nombre_columnas()
</p>
5. Se verifica que las columnas con información numerica cómo número de Accesos, estén en formato número, de no ser asi, se les cambia el type.  ➡️ Función de_object_a_numerica()
</p>
6. Algunas tablas están un formato horizontal por lo que requieren ser transpuestas para lograr un mejor manejo y análisis de la data.
</p>
7. A las tablas con columnas de Año y Trimestre se les agrega una columna "Fecha" en formato datetime concatenando los datos de año y trimestre.
</p>
8. Se analizan y eliminan los outliets. Primero se presentan visualmente en un grafico de cajas y bigotes, y luego se analizan numericamente con la metodología de z-score. ➡️ Funciones grafico_outliers() , detectar_outliers() , eliminar_outliets()
</p>
9. Se hace un describe para ver la información de estadísitica básica de las variables numéricas.
</p>
10. En algunas tablas se requieren transformaciones especificos a los datos y se realzian según sea en caso.
</p>

Finalmente, los archivos limpios y listos para ser utilizados en el dashboard son exportados en formato CSV en la carpeta /Data fuente Dashboard

Nota:  👁️ Con el fin de Agilizar el proceso de Limpieza se crean las funciones anteriores.


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

***Conclusión EDA:*** 

De la información suministrada encontramos:

Los siguientes dataset nos dan un contexto de los datos pero al no tener escala de tiempo su información nos sirve para darnos contexto:

- data_acc_vel_loc_sinr 
- data_acc_tec_loc 

Los siguientes Dataset nos presentan información muy completa y nos permite generar los KPI:

- data_pen_hogares  
- data_pen_poblacion 
- data_ingresos
- data_acc_por_tecn 

</p>

Los siguientes Dataset nos presentan información para calculo de otras métricas:

- data_dial_BAf.to_csv('./Data fuente Dashboard/Dial-BAf.csv') 
- data_Vel_sin_r.to_csv('./Data fuente Dashboard/Velocidad_sin_Rangos.csv')  # 2
- data_vel_prc_prov.to_csv('./Data fuente Dashboard/Velocidad % por prov.csv')  # 3
- data_total_VMD.to_csv('./Data fuente Dashboard/Totales VMD.csv')  # 4 

</p>

Finalment, encontramos información redundante la cual no se requiere en el dashboard:

- data_total_Dial_BAf
- data_pen_total
- data_total_acc_por_vel
- data_acc_por_vel

</p>

**3. Generación del DashBoard:**

El Dashboard se generó en la herramienta :atom: PowerBI :atom:. 
Inicialmente se suben los archivos fuente con PowerQuery, donde se hace un ajuste en el formato de los datos.
Ya en Power BI se crean las relaciones entre tablas, la tabla calendario (jerarquia de fechas), y la tabla de métricas, dejando la información lista para ser modelados.
</p>
En el dashboard se siguió el siguiente hilo conductor para su realización. Inicialmente se realiza una hoja de análisis para cada una de las variables seleccionadas. Finalmente se definen los 4 KPI y se resumen en una hoja inicial.
</p>
Hojas de Análisis de variables:
</p>

- **P. Hogares:** Se analiza a detalle la penetración entendida como el porcentaje de hogares o individuos que tienen acceso a internet en una determinada área geográfica, medida en términos de hogares.  En la parte superior se ve la evolución de este indicador trimestre a trimestre, en la parte inferior se muestra la info a modo de tabla y finalmente se grafica la variación porcentual trimestral del indicador. Esta hoja soporta el 1er KPI
- **P. Población:** Se analiza a detalle la penetración alacceso a internet en términos de hogares.  En la parte superior se ve la evolución de este indicador trimestre a trimestre, en la parte inferior se muestra la info a modo de tabla y finalmente se grafica la variación porcentual trimestral del indicador. Esta hoja soporta el 2do KPI.
- **Ingresos:** Los ingresos son un factor clave en el exito/fracaso de las compañias, por lo que siempre debe ser incluido en el Balanced Scored Card (BSC) de las mismas. En este caso, se grafica su evolución trimestral. La variacion trimestral de Ingresos se define como 3er KPI.
- **Accesosp por Fibra Optica:** Se analiza el número de conexiones a internet registradas, a  través de las tecnologías ADSL, fibra óptica, cable módem, Wireless y Otros, con el fin de ver si comportamiento y poder detectar oportunidades en el mercado. Se seleccionan las conexiones por fibra optica por su rápido crécimiento en los últimos años en Argentina, adicionalmente es una tecnologia que ofrece velocidades de conexión mucho más altas y estables en comparación con otras tecnologías como ADSL y Cable Modem. Lo que es crucial para satisfacer la creciente demanda. De este sale el 4to y ultimo KPI.
- **VMD:** Finalmente se analizan las conexiones por tecnologías obsoletas lo cual representa una oportunidas en la medida en que puedan ser reemplazados por fibra-optica. De esta hoja no se generó un KPI debido que la compañía no maneja directamente estas tecnologías.
</p>

- **Hoja Dashboard KPI´s:** Se diseña en una hoja con el resumen del cumplimiento de la meta de los KPI´s anteriormente mencionados.
</p>
 La siguiente imagen presenta la hoja principal de indicadores.
 
<img src ="/Imagenes/Grafica 3.png">

Para cada KPI se muestra:

- Nombre del Indicador
- Tarjeta del KPI donde se presenta el valor relativo del cumplimiento Vs el objetivo.
- Gráfico de Medidor del valor absoluto del indicador. En este se presenta el valor y la meta en la unidad inicial, por ejemplo número de conexiones, pesos, entre otros.
- Grafica de tendencia del valor del KPI. Muestras para los 2 ultimos años (o los que se seleccionen en el slicer de la parte superior), el valor trimestre a trimestre del indicador.

   </p>
### 👀 Diseño de KPI´s: 👀 

Los anteriores KPI se están calculando con la información del sector, y por tanto su utilidad sería la de monitorear el sector. 
Para hacerlos aplicables a la compañía, requieren ser adaptados a las cifras propias de la compañía asi: 
</p>

- **Penetración Hogares:** por parte de los productos de internet de la compañía. La meta podria mantenerse en el valor estipulado. Su estrategia de cumplimiento deberia enfocarse en encontrar nuevos clientes.
- **Penetración Población:** por parte de los productos de internet de la compañía, es complementario al de hogares, en la medida que se logre tener mas de un servicio de conexión por hogar. Su estrategia estaría marcada hacia incrementar los servicios en los clientes actuales.
- **Ingresos:** Se medirían los ingresos operacionales de la compañía con metas puntuales definidas por geografia y producto en un marco de tiempo.
- **Accesos por Fibra Optica:** En este indicador se requiere analizar la cantidad de accesos de los clientes de la compañia a través de la tecnología fibra optica. La estrategía se debe enfocar en reemplazar otras tecnologias, en clientes actuales o nuevos, por la de fibra óptica.
  </p>

 ## ANALISIS Y CONCLUSIONES: 
</p>

**Penetración Hogares:**  </p>
Cómo ya se mensionó en este documento, la penetració es el porcentaje de hogares o individuos que tienen acceso a internet en una determinada área geográfica. Se puede medir en términos de penetración en la población o en los hogares.
En el caso de Argentina la penetración del servicio de internet por hogares tiene una tendencia constante al alza. En el 1er trimestre de 2024 alcanzó un total del 72,04 por cada 100 hogares o del 72,04% que es lo mismo. El incremento en el indicador para todo el 2023 fue del 1,07% frente a un 1,59% del 2022. Para el 2024 se espera alcanzar un 2% trimestral, sin embargo en el 1er trimestre el escenario nos es alentador ya que solo se logro un 0,05% de crecimiento.
</p>
<img src ="/Imagenes/Grafica Hogares.png">
</p>

**Penetración Población:** </p>
El indicador de penetración medida en términos de población tiene una tendencia al alza un poco más marcada que la medida en términos de hogares, sin embargo en terminos porcentuales es mucho menor, para el 1er trimestre de 2024 alcanzó en Argentina un 20,1%. El crecimiento del indicador en el año 2023 fué de 1,31%.
</p>
<img src ="/Imagenes/Grafica Poblacion.png">
</p>

**Ingresos:** </p>
Los Ingresos del sector en total para el año 2023 en Argentina ascendieron a 522,6 MM y para el primer trimestre de 2024 a 280,4 MM de pesos lo que presenta un buen pronóstico para el año. Las grandes perspectivas de crecimiento del sector son un alisciente para invertir en el mismo.
La Meta del indicador se define conservadoramente en un 15% dada la gran dinámica del sector.
</p>
<img src ="/Imagenes/Grafica Ingresos.png">
</p>

**Accesos por Fibra Optica:** </p>
Cómo ya se mensionó en este documento, se seleccionan las conexiones por fibra optica por su rápido crécimiento en los últimos años en Argentina, adicionalmente es una tecnologia que ofrece velocidades de conexión mucho más altas y estables en comparación con otras tecnologías como ADSL y Cable Modem. Para el año 2023 se dieron 7,6 millones de conecciones por fibra optica, en el 1er trimestre del 2024 fueron de 2,2 millones, valor que aunque decrece con respecto al 4to trimestre de 2023, presenta una muy buena perspectiva de crecimiento.
<img src ="/Imagenes/Grafica FO.png">
</p>
</p>


