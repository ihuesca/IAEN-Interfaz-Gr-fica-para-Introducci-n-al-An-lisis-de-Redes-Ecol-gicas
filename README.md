# **IAEN: Interfaz Gráfica para Introducción al Análisis de Redes Ecológicas** 

## **1 Instroducción**



Con la finalidad de hacer accesibles a todos los usuarios a las distintas rutinas del lenguaje R para el análisis estadístico de redes y sus gráficas sin la necesidad de un conocimiento en programación se programó una interface gráfica para el usuario (GUI). 

El paquete **IAEN** es una herramienta que proporciona una interfaz gráfica de usuario (GUI) la cual está implementada mediante el kit de herramientas **GTK+** implementado en el paquete **RGtk2** y está almacenado en el repositorio de GitHub. Permite gestionar datos y realizar diferentes tipos de herramientas empleados en el análisis de redes ecológicas, así como de visualización y edición de gráficos. Existe un gran repertorio de paquetes implementados en R que hacen hincapié en el análisis de redes ecológicas para matrices adyacentes binarias, ponderadas y bipartitas. R también cuenta con un conjunto de paquetes que permiten analizar y visualizar diferentes tipos de redes en general, cada uno tiene sus diferentes formas de gestionar las bases de datos. 

Por lo mencionado anteriormente, ésta interfaz está integrada por diversos paquetes almacenados en R que hacen énfasis en redes ecológicas y redes en general, permitiéndonos hacer uso de funciones de manera fácil e interactiva sin que el usuario emplee por completo el lenguaje de programación de R. Se emplean métodos básicos y usuales en el que se especifica en cada proceso el paquete que se está utilizando con la finalidad de difundir el uso de R y sus paqueterías, donde si se desea hacer un análisis más específico puede consultar las diferentes funciones incluidas en el entorno R. 

Este documento está destinado a auxiliar al usuario en el funcionamiento de la interfaz para hacer uso adecuado de las diferentes herramientas que proporciona. También se describe cada una de las ventanas que la conforman. En general el usuario puede importar bases de datos en la pestaña de “*File*”, efectuar análisis de redes en la ventana de “*Statistics*”, crear redes binarias y realizar funciones de mundos pequeños en la ventana de “*Simulations*” y ejecutar gráficos en la ventana de “*Graphs*”. 

## **2 Dependencias**



La lista de dependencias que se requieren para que la interfaz se ejecute correctamente se enlista en la Tabla 1, así como el motivo para la que fueron utilizados. Cabe mencionar que existe una alta dependencia de los paquetes enaR, cheddar y bipartite debido a que son los paquetes que más hacen énfasis en la temática de redes ecológicas, además de que contienen funciones de interés para nuestro objetivo. Sólo algunas funciones fueron implementadas. Respecto a la realización de gráficos algunos de éstos fueron realizados mediante las funciones por defecto de su paquete, mientras que otros fueron efectuados empleando los paquetes ggplot2, gplots y ggraph para mejorar en algunos casos su resolución. 



Tabla 1. Lista de paquetes requeridos 

| Paquetería                        | Descripción                                           |
| --------------------------------- | ----------------------------------------------------- |
| RGtk2 (Lawrence and Temple, 2010) | Herramientas para la creación de interfaces gráficas  |
| cairoDevice (Lawrence, 2017)      |                                                       |
|                                   |                                                       |
| enaR (Lau et al., 2017)           | Funciones para análisis redes ecológicas              |
| cheddar (Hudson et al., 2018)     |                                                       |
| bipartite (Dormann et al., 2008)  |                                                       |
|                                   |                                                       |
| readxl (Wickham and Bryan, 2018)  | Importación y exportación de datos                    |
| writexl (Ooms, 2018)              |                                                       |
|                                   |                                                       |
| network (Butts, 2015)             | Funciones para análisis de redes en general           |
| igraph (Csardi and Nepusz, 2006)  |                                                       |
| sna (Butts, 2016)                 |                                                       |
| tnet (Opsahl, 2009)               |                                                       |
|                                   |                                                       |
| ggplot2 (Wickham, 2016)           | Funciones para la edición y visualización de gráficos |
| ggraph (Pedersen, 2018)           |                                                       |
| gplots (Warnes et al., 2016)      |                                                       |
| scales (Wickham, 2017)            |                                                       |
|                                   |                                                       |
| reshape (Wickham, 2007)           | Reestructura de datos                                 |
|                                   |                                                       |
| pryr (Wickham, 2018)              | Crear enlaces activos                                 |
|                                   |                                                       |

## **3 Cargar la Interfaz**



Una vez que se llevó a cabo el proceso de instalación del paquete y verificado que se haya realizado exitosamente, los pasos que prosiguen son los siguientes: en primer lugar hay que cargar el paquete y posteriormente utilizar la función correspondiente para poder visualizar la interfaz. La instalación sólo se realiza una vez en cada versión instalada de R o en su caso R-Studio, así como para cargar el paquete sólo se hace una vez en cada espacio de trabajo abierto, tal como se muestra a continuación:



```bash
library(IAEN)
IAEN()
```



| ![GUI](/Users/israelhuesca/Desktop/GitHub projects/GUIimages/GUI.PNG) | ![Data](/Users/israelhuesca/Desktop/GitHub projects/GUIimages/Data.PNG) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![Result](/Users/israelhuesca/Desktop/GitHub projects/GUIimages/Result.PNG) |                                                              |

Figura 1: Interfaz gráfica de usuario



En la *Figura 1* se ilustra la estructura interactiva de la interfaz gráfica cuando ha sido cargada en la consola de **R-Studio** donde se observa que los elementos que la componen son una barra de menú, una barra de accesos directos para opciones rápidas de importación y exportación de datos, un conjunto de pestañas que incluye una presentación, una pestaña llamada ”*Data*” donde se pueden visualizar los datos que han sido cargados y una pestan ̃a nombrada ”*Result*” donde a través de sub-pestañas se muestran las diferentes salidas de los análisis realizados.

En la barra de menú se muestran diferentes pestañas agrupadas por el tipo de funciones tales como la pestaña de ”*File*” que contiene funciones de importación y exportación de datos. La pestaña de ”*Statistics*”, contiene funciones de análisis de datos para las diferentes tipos de redes (binaria, ponderada y bipartita). La pestaña de ”*Simulation*” muestra una ventana con opciones para crear diferentes tipos de redes alimenticias y realizar funciones utilizadas en mundos pequeños. La pestaña de ”*Graphs*” muestra una gama de gráficos que se pueden realizar para los diferentes tipos de redes. Por último la pestaña de ”*Help*” proporciona información general del paquete.

## **4 Importación de datos**



- *Matriz adyacente de una red ponderada*

Antes de cargar una matriz ponderada hay que tener en cuenta la estructura en la que se requiere que estén organizados los datos. Dicha estructura está basada en los argumentos de entrada requeridos en la función **enaR::pack** para crear un objeto de clase red y para poder cargarla y visualizarla en la interfaz interactiva se requieren las siguientes especificaciones:

-- Nombres de matriz de adyacencia iguales para filas y columnas, preferentemente no numérica y sin espacios.

-- Contener valores numéricos.

-- Evitar celdas vacías.

-- Incluir una columna que especifique los nodos vivos (1) y los no vivos (0).

-- Vectores de entradas, exportaciones, salidas, respiraciones, biomasas y vivos deben ser colocadas verticalmente a la matriz de adyacencia y en ese orden.

-- La columna Outputs es la suma de respiraciones y exportaciones, este vector es opcional.

-- La matriz adyacente, el vector de entradas, exportaciones y el vector de vivos son obligatorios, los demás pueden o no considerarse. En caso de no considerarlos incluir un vector de ceros para evitar valores vacíos.







