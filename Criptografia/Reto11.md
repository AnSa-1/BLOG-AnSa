# reto11_colegio 

Después de conseguir sacar la contraseña del usuario bill, la profesora felicita y os reenvía otro mensaje de antiguos alumnos que actualmente trabajan en el mundo de la ciberseguridad. 

Está segura de que todo el COLEGIO está muy contento con el trabajo de estos exalumnos. 

Pregunta: 
¿Qué mensaje enviaron estos antiguos alumnos? 
 
 **DATOS**
 
 Fichero imagen. 
 
 ![image](https://user-images.githubusercontent.com/69391590/124316347-622d8280-db6d-11eb-8ef7-295417895954.png)
 
 
 Nos proporcionan una imagen que identificamos con símbolos. Después de una búsqueda en internet y descartar “Pidgeon Cipher”, podemos encontrar en la web de “doce.fr” una herramienta “Rosicrucian cipher” para sustituir símbolos y caracteres
 
 ![image](https://user-images.githubusercontent.com/69391590/124316422-7cfff700-db6d-11eb-8b40-ef789049c294.png)

El resultado son los siguientes caracteres.

```noqpgosuzzwkfonixruacuglpalop```

El enunciado indica en mayúsculas que los exalumnos del COLEGIO han hecho un buen trabajo. Al estar resaltada esa palabra, podemos pensar que puede ser una clave para descifrar el texto de arriba. Tras probar algunos algoritmos de cifrado clásico como César sin éxito, probamos con Vignere con clave “COLEGIO”. El resultado es la solución

http://rumkin.com/tools/cipher/vigenere-keyed.php

![image](https://user-images.githubusercontent.com/69391590/124316900-35c63600-db6e-11eb-8767-a27096ce60d3.png)

 flag{laflageslosexalumnosossaludan}
 
 ## PISTAS
 
 Pista 1: Los símbolos representados sustituyen a letras. Cifrado de sustitución.
 
 Pista 2: El primer cifrado es Rosicrucian (https://www.dcode.fr/rosicrucian-cipher).
 
 Pista 3: El segundo es Vignere. El nombre del fichero tiene su importancia.
