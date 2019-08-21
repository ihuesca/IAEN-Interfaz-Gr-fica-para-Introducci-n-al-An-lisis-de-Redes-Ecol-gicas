# **IAEN: Interfaz Gráfica para Introducción al Análisis de Redes Ecológicas** 

## **1 Instroducción**



Con la finalidad de hacer accesibles a todos los usuarios a las distintas rutinas del lenguaje R para el análisis estadístico de redes y sus gráficas sin la necesidad de un conocimiento en programación se programó una interface gráfica para el usuario (GUI). 

El paquete **IAEN** es una herramienta que proporciona una interfaz gráfica de usuario (GUI) la cual está implementada mediante el kit de herramientas **GTK+** implementado en el paquete **RGtk2** y está almacenado en el repositorio de GitHub. Permite gestionar datos y realizar diferentes tipos de herramientas empleados en el análisis de redes ecológicas, así como de visualización y edición de gráficos. Existe un gran repertorio de paquetes implementados en R que hacen hincapié en el análisis de redes ecológicas para matrices adyacentes binarias, ponderadas y bipartitas. R también cuenta con un conjunto de paquetes que permiten analizar y visualizar diferentes tipos de redes en general, cada uno tiene sus diferentes formas de gestionar las bases de datos. 

Por lo mencionado anteriormente, ésta interfaz está integrada por diversos paquetes almacenados en R que hacen énfasis en redes ecológicas y redes en general, permitiéndonos hacer uso de funciones de manera fácil e interactiva sin que el usuario emplee por completo el lenguaje de programación de R. Se emplean métodos básicos y usuales en el que se especifica en cada proceso el paquete que se está utilizando con la finalidad de difundir el uso de R y sus paqueterías, donde si se desea hacer un análisis más específico puede consultar las diferentes funciones incluidas en el entorno R. 

Este documento está destinado a auxiliar al usuario en el funcionamiento de la interfaz para hacer uso adecuado de las diferentes herramientas que proporciona. También se describe cada una de las ventanas que la conforman. En general el usuario puede importar bases de datos en la pestaña de “*File*”, efectuar análisis de redes en la ventana de “*Statistics*”, crear redes binarias y realizar funciones de mundos pequeños en la ventana de “*Simulations*” y ejecutar gráficos en la ventana de “*Graphs*”. 

## **2 Dependencias**



La lista de dependencias que se requieren para que la interfaz se ejecute correctamente se enlista en la Tabla 1, así como el motivo para la que fueron utilizados. Cabe mencionar que existe una alta dependencia de los paquetes enaR, cheddar y bipartite debido a que son los paquetes que más hacen énfasis en la temática de redes ecológicas, además de que contienen funciones de interés para nuestro objetivo. Sólo algunas funciones fueron implementadas. Respecto a la realización de gráficos algunos de éstos fueron realizados mediante las funciones por defecto de su paquete, mientras que otros fueron efectuados empleando los paquetes ggplot2, gplots y ggraph para mejorar en algunos casos su resolución. 



Tabla 1. Lista de paquetes requeridos 

