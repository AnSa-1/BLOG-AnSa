#  reto01_Quijote


Desde la creación del instituto, algunos alumnos se han encargado de la gestión del periódico local, "El noticiero", donde se intercambian mensajes y escriben artículos didácticos. En uno de los artículos alguien anónim@ ha lanzado un reto. Asegura haber escondido un mensaje en el libro más universal de la literatura, pero solo nos proporciona algunas coordenadas para que las mentes más brillantes del instituto puedan resolverlo.

Datos proporcionados:  Libro: "El quijote de la mancha" (adjunto) 
Cada una de etas coordenadas pertenece a una palabra, júntalas mediante un guion bajo “_”. 
Si encuentras “palabra1” y “palabra2” la solución es flag{palabra1_palabra2}. 

**DATOS**






- 10: 8:2  
-  23:10:1      
- 30:8:2  
- 30: 26:7  
- 35:1:7
- 151:19:10
- 151:11:8 
- 152:11:5   

Para poder resolver el reto debemos ir coordenada a coordenada aplicando cada palabra y concatenándola con un guion bajo.
Por ejemplo, si buscamos página 10, línea 8 y posición 2 la palabra es “querer”. 
![image](https://user-images.githubusercontent.com/69391590/123652833-8d8a3780-d824-11eb-813d-0feb3814f729.png)

La correspondencia página, línea y posición en el libro proporcionado es la siguiente:  
 

- 10: 8:2 → querer 
-  23:10:1  → saberr
- 30:8:2  → noticia
- 30: 26:7  → sobre
- 35:1:7→ conocer
- 151:19:10→ misterio
- 151:11:8 → quien 
- 152:11:5 → hizo
Si realizamos la misma operación con el resto de coordenadas, la solución es: 
 
flag{querer_saber_noticia_sobre_conocer_msiterio_quien_hizo} 


## PISTAS
Pista 1: Se entregan coordenadas para aplicar el cifrado “Book cipher”.  
Pista 2: Corresponden a “página:línea:posición de palabra”.  
Pista 3: La primera palabra es “querer”.   
