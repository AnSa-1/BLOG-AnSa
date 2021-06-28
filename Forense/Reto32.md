# reto32_MensajeOculto 

Como ejercicio final del módulo de forense, el profesor de informática ha propuesto la siguiente actividad: Descifrar el contenido del mensaje oculto en el fichero Mensaje.zip. Para ellos tenemos una captura de tráfico y el propio fichero. 

Pregunta:

¿Aprobarás este módulo? 

**DATOS**

Dos ficheros: Fichero pcap y fichero zip. 

Descargamos los ficheros. Intentamos descomprimir el fichero Mensaje.zip pero nos solicita contraseña:


```──(root@kali)-[~/] 
└─# unzip Mensaje.zip  
Archive:  Mensaje.zip 
[Mensaje.zip] Mensaje.pdf password:  
password incorrect--reenter:  
password incorrect--reenter:  
   skipping: Mensaje.pdf            
				 incorrect password ```


Analizando el pcap, vemos que predomina tráfico HTTP entre dos IPs concretas: 192.168.209.128 y 192.168.209.141, en la que el primero es el servidor y el segundo es el cliente

![image](https://user-images.githubusercontent.com/69391590/123714135-a9fe9200-d86d-11eb-996e-66d8b50a31d9.png)

Si nos fijamoos en el paquete número 16 se hace una petición POST al recurso “/html/index.php” con parámetros GET que contiene lo que parece una sentencia SQL, aparecen palabras del tipo SELECT y UNION: 

![image](https://user-images.githubusercontent.com/69391590/123714180-be428f00-d86d-11eb-87a0-5270125b7613.png)

Si buscamos dentro del tráfico palabras típicas de consultas a bases de datos como SELECT, encontramos que existen muchos paquetes que contienen esa cadena, analizamos los de mayor tamaño para ver la respuesta: 


![image](https://user-images.githubusercontent.com/69391590/123714244-da463080-d86d-11eb-8958-eb6ab1a16654.png)



