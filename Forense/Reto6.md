# reto06 Acceso_FTP 

Parece que alguien desde una cuenta anónima está intentado ayudar en la investigación y os ha enviado otro fichero pcap. Lo ha capturado desde alguna clase de informática que se dio en el instituto. 

Pregunta:   

Hay varias tramas que se corresponden a una subida FTP. Nos piden encontrar el contenido de lo que se ha descargado para proseguir en la investigación. Se trata de un fichero que se han descargado.

**DATOS**

Fichero pcap descargable. 

Abrimos el fichero pcap con Wireshark. Identificamos que ha sido capturado a nivel de protocolo. Para ello, accedemos a Estadísticas -> Jerarquía de Protocolo 

![image](https://user-images.githubusercontent.com/69391590/123676788-47d96900-d83c-11eb-9733-f6beb30dc67c.png)

En la ventana de estadísticas vamos a aplicar un filtro sobre el protocolo DNS

![image](https://user-images.githubusercontent.com/69391590/123676858-5aec3900-d83c-11eb-8fa5-ec44eec6aba6.png)

Al tener el filtrado el tráfico procedemos a ver las acciones realizadas en el servidor FTP. Para ello nos colocamos en una de las tramas para hacer clic en botón derecho y “Seguir->Flujo TCP”.

![image](https://user-images.githubusercontent.com/69391590/123676972-78b99e00-d83c-11eb-9a39-0baf0767e147.png)


Se nos abrirá una ventana con las acciones realizadas. Si nos fijamos se descarga un fichero “flag.zip” y otro passwords.txt. 

![image](https://user-images.githubusercontent.com/69391590/123677060-925ae580-d83c-11eb-95e6-258c83409948.png)


Hacemos uso de “strings” y “binwalk” para extraer su contenido 

```strings evidencias.pcap```


Vemos el momento exacto y el modo de conexión, así como el contenido de passwords.txt.


![image](https://user-images.githubusercontent.com/69391590/123677383-f382b900-d83c-11eb-9caa-29210e18626a.png)


Guardamos este fichero para “crackear” la contraseña del fichero flag.zip. Ejecutamos la herramienta binwalk con el parámetro “-e (extract)” que recorrerá el fichero buscando cabeceras conocidas y volcando su contenido a un directorio.

```binwalk -e evidencias.pcap```

Vemos que disponemos del fichero flag.zip y que este está protegido mediante contraseña.

![image](https://user-images.githubusercontent.com/69391590/123677618-40ff2600-d83d-11eb-9abe-25f89f8a57c1.png)


Vamos a poner en bucle las claves abriendo el zip. 

```for clave in $(cat passwords.txt); do echo $clave; unzip -P $clave 1178.zip; done```

![image](https://user-images.githubusercontent.com/69391590/123677842-80c60d80-d83d-11eb-9dac-f81a2e4d7fe5.png)


La contraseña es “karina” y el contenido del fichero flag.txt es el siguiente. 

![image](https://user-images.githubusercontent.com/69391590/123677960-a2bf9000-d83d-11eb-8768-ead3a9f02a34.png)

flag{ftp_stream_pcap_with_credentials!}

## PISTAS

 Pista 1: Utiliza Wireshark para abrir el fichero. Mira en  Estadísticas->Jerarquía de Protocolo. 
 
Pista 2: Filtra por consultas al “File Transfer Protocol”  (FTP) y observa acciones realizadas. 

Pista 3:   Se han descargado dos ficheros: flag.zip y passwords.txt. Flag.zip está protegido con alguna de las contraseñas de passwords.txt.

