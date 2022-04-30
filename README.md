# Proyecto Sistemas de Información

-----------------------------------------------------------------------------------------------------------
### Identificar cuáles son las localidades que menos acceden a los beneficios de la implementación de microchip en mascotas
-----------------------------------------------------------------------------------------------------------

## 1. Introducción
El Instituto de Protección Animal (IDPYBA) tiene el servicio de implantación de microchip para identificar a perros y gatos que conviven como animales de compañía de los residentes en Bogotá.
El microchip es un dispositivo electrónico del tamaño de un grano de arroz que se implanta en la parte superior del cuello del animal, debajo de su piel. Está encapsulado en una cámara de cristal y recubierto con una capa de parylene (similar al latex), la cual hace que al entrar en contacto con el organismo quede fija en esa área y no se desplace por el cuerpo. El microchip contiene un número único de 15 dígitos que identifica, como una cédula, a cada animal y a su respectivo propietario.

La persona interesada debe llenar un formulario con su información personal y datos de contacto junto con los datos de su perro o gato (como nombre, raza, edad, sexo, entre otros). Esta información se registra en la plataforma web www.ciudadano4patas.com y se asocia con el número de 15 dígitos contenido en el dispositivo implantado. De esta manera, utilizando un lector de microchips se identifica ese número y se puede consultar en el sistema los datos del animal y su tenedor. Este proceso hace parte del programa de identificación, registro y monitoreo de animales domésticos llamado Ciudadano de 4 Patas, del IDPYBA.

Si tu amigo peludo se aleja un día y tiene la suerte de ser encontrado por un extraño amable, todo lo que tiene que hacer esta persona es entregar a tu perro a un refugio de rescate o clínica veterinaria donde el personal o el veterinario usarán un dispositivo de escaneo para verificar si tu perro cuenta con microchip. El escaneo no causará estrés adicional a tu perro y es completamente indoloro.


## 2. Herramientas utilizadas

* **Pandas:** Pandas es una biblioteca de Python que se especializa en manipular y analizar estructuras de datos al proporcionarlas de manera similar a los marcos de datos R. Pandas se basa en Numpy, una biblioteca que agrega potentes tipos de matrices a Python. Los principales tipos de datos que pueden ser representados por pandas son:

  *  Datos tabulares con columnas de tipo heterogéneo con etiquetas en columnas y filas
  *  Series temporales
  
  Pandas proporciona herramientas que permiten:

  * Leer y escribir datos en diferentes formatos: CSV, Microsoft Excel, Bases SQL y formato HDF5
  * Fusionar y unir datos
  * Seleccionar y filtrar de manera sencilla tablas de datos en funcion de posición, valor o etiquetas
  * Transformar datos aplicado funciones tanto en global como por ventanas
  * Manipulación de series temporales
  * Hacer gráficas

* **Power BI:** Es una aplicación de servicio basada en la nube que ayuda a recopilar, administrar y analizar datos de varias fuentes a través de una interfaz fácil de usar. Recopile datos y procéselos, convirtiéndolos en información comprensible, utilizando gráficos y cuadros visualmente atractivos y fáciles de procesar. Esto permite a los usuarios generar y compartir una instantánea clara y útil de lo que sucede en su proyecto o negocio.

  Power BI se utiliza para ejecutar informes basados en los datos anteriores de la empresa, el negocio o el proyecto. Puede conectarse a una amplia gama de conjuntos de  datos, y ordena genera información y elementos visuales a partir de estos datos, también ayuda a los usuarios a ver no solo lo que sucedió en el pasado y lo que está sucediendo ahora, pero también sobre lo que podría suceder en el futuro.

  Beneficios del uso de Power BI:
 
   * Las empresas pueden gestionar  grandes cantidades de datos en Power BI que muchas otras plataformas tendrían dificultades para procesar
   * Power BI está basado en la nube, por lo que los usuarios obtienen capacidades de inteligencia de vanguardia y algoritmos potentes que se actualizan periódicamente
   * Power BI tiene una interfaz intuitiva que lo hace mucho más fácil de usar y fácil de navegar que las hojas de cálculo complejas
   *  Power BI garantiza que los datos estén seguros, ofreciendo controles de accesibilidad tanto interna como externa
 

## 3. Contexto del problema

El extravio de mascotas es una problematica que tiene diversos factores por los cuales pueden ocurrir, desde el descuido de los dueños, hasta el robo por parte de terceroe. Desde la iniciativa "Ciudadano de 4 Patas" por parte de la alcaldia de Bogotá, se desea dar una solucion a este problema en el que por medio de microships identificados cadada uno con un nomuero unico de 15 digitos permite identificar a la mascota por medio de radiofrecuencias. La finalidad de este proyecto es identificar, realizar un seguimiento y registro de loas mascotas que se encuentran presentes en la ciudad.

Sabiendo esto se desea reconocer cuales son las carateristicas por las cuales los ciudadanos de diferentes localidades y estratos accedieron a este servicio en un periodo de 10 años (entre 2009 y 2019), de igual forma identificar si las especies, razas o sexo de las mascotas son factores que pueden generar que haya un mayor o menor uso de ese servicio por parte de la comunidad. 


## 4. Solución del problema
Por medio de un dasboard se realizo un respectivo una investigación detallado del Instituto Distrital de Bienestar Animalobtenido de la pagina https://www.animalesbog.gov.co/. Esto es con el fin de identificar que localidades acceden a los beneficios de implantarles el microchip o esterilizar a las mascotas. De tal manera con la ayuda de las herramientas Pandas (Python), Power Bi, asi mismo con ayuda de estas herramientas se oodra observan cualquier información que permita identificar en que localidades hacen mas uso de estos servicios y para que mascotas. 

Lo primero que hicimos fue plantear las preguntas de negocio que nos ayudara a identificar.

## 5. Preguntas de negocio

1. ¿Cuál es el nombre que más se repite en la espacie de felinos por localidad? 

 * pet['NOMBRE ANIMAL'].value_counts().idxmax()
   
2. ¿Cuál es la raza más común de la localidad de suba?

 * if(pet.LOCALIDAD == 'Suba') pet['RAZA'].value_counts().idxmax()

3. ¿Cuantos caninos hay en ciudad bolívar con estrato 3? 
* p = len(pet[(pet.LOCALIDAD == 'Ciudad Bolívar') & (pet.ESTRATO == 3) & (pet.ESPECIE == 'Canino')])
print("El total de caninos es de:", p)

4. ¿Cual es el total de felinos por sexo en la localidad de chapinero? 
* p = len(pet[(pet.ESPECIE == 'Felino') & (pet.LOCALIDAD == 'Chapinero')])
print("El total de felinos por sexo es:", p)

5. ¿Cuál es el total de felinos y caninos de raza criollo por localidad?
* p = len(pet[((pet.ESPECIE == 'Felino') | (pet.ESPECIE == 'Canino')) & (pet.RAZA == 'CRIOLLO')])
print("Total de caninos y felinos por localidad con raza criolla es:", p)

6. ¿Cuántos microships se usaron por estrato?  
* p = len(pet)
print("Cantidad de microships usados por estrato:", p)

7. ¿Cuantos caninos de raza PUG hay en estrato 3 o menor a ese estrato? 
* p = len(pet[(pet.ESPECIE == 'Canino') & (pet.RAZA == 'PUG') & (pet.ESTRATO <= 3)])
print("Cantidad de Raza pug:", p)

8. ¿En qué año se implementó más el microchip por especie? 
 * pet['FECHA REG. IMPLANTE'].value_counts()
  
9. ¿Cual es el porcentaje por sexo y año de los caninos? 
 * p = len(pet[(pet.ESPECIE == 'Canino')])
  v = len(pet)
  x = (p / v) * 100
print("El procentaje de caninos es: ", x)

10. ¿Cuantos felinos no esterilizados hay en la localidad de Bosa? 
 * p = len(pet[(pet.ESPECIE == 'Felino') & (pet.LOCALIDAD == 'Bosa') & (pet.ESTERILIZACION == 'NO REGISTRADA')])
print("Hay una cantidad de: ", p)

11. ¿Cuantos felinos por sexo hay en el archivo?
* p = len(pet[(pet.ESPECIE == 'Felino')])
print("Hay una cantidad de felinos de: ", p) 

12. ¿Cuantos Golden retriever hay por localidad?
* p = len(pet[(pet.RAZA == 'GOLDEN RETRIEVER')].LOCALIDAD)
print("Por localidad hay un total de Golden Retriever de: ", p)

## 6 Muestra de Datos
Luego se hizo el dashboard con la ayuda de la herramienta de Power BI se visualizara acontinuación:

[![Microships.png](https://i.postimg.cc/gkx58nxZ/Microships.png)](https://postimg.cc/bsj3jYHy)
[![Captura-de-pantalla-2022-04-29-195756.png](https://i.postimg.cc/TY19Wg5V/Captura-de-pantalla-2022-04-29-195756.png)](https://postimg.cc/56cvhH3y)
[![Captura-de-pantalla-2022-04-29-200030.png](https://i.postimg.cc/Y0WCJdyN/Captura-de-pantalla-2022-04-29-200030.png)](https://postimg.cc/gLGphHpr)
[![Captura-de-pantalla-2022-04-29-200209.png](https://i.postimg.cc/ZKmByy7f/Captura-de-pantalla-2022-04-29-200209.png)](https://postimg.cc/w3WTC3dJ)

## 7 Analisis
## 8 Conclusiones

Podemos concluir que de toda la información que hemos obtenido, afirmar que los medios de identificación de animales son capaces de prevenir el robo o tráfico ilícito, así como su abuso e irracionalidad, al garantizar la capacidad de vincular inequívocamente a los animales con sus dueños. Hay que aclarar que el  microchip  sirve  como  un  reconocimiento  legal  el  cual  tiene  como  objetivo  identificar,  registrar  y  realizar  seguimiento  a  los  animales  de  compañía  que  habitan  en  la ciudad. Ayudar a los perritos que son abandonados identificándolos por medio del microchip todos los datos correspondientes al animal y de su responsable. Así mismo facilita la búsqueda de los perritos perdidos. 

El microchip implantado en la mascota es un medio de identificación, que puede proporcionar la garantía antes mencionada y lograr efectivamente el propósito del medio de identificación. Dado que el microchip puede almacenar un número de identificación único para cada animal, nos permite distinguirlo de otros animales y asociarlo con datos específicos, como la propiedad y la dirección. Usando los datos disponibles en Open Data Bogotá, nuestro equipo pudo identificar diferentes factores a analizar, incluyendo la ubicación, clase, raza, género y especie de la mascota, y de esta manera, explicamos el mayor uso de mascotas en microchips. Teniendo en cuenta la combinación de datos

