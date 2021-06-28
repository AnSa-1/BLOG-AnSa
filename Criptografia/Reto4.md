# reto04 enigma

Con la información que habéis obtenido, intenta utilizar las credenciales para poder acceder al ordenador del periódico y al entrar os descargáis un archivo.

El fichero original ha cifrado alguna información secreta que debes obtener para que la investigación no se atasque. Esto es lo que sabemos que ha devuelto la salida del fichero que has obtenido al entrar en la web del periódico.

**DATOS**

Hemos recibido este mensaje junto a unas instrucciones para su manejo. Parece un completo enigma.

59556843656d517a545764684d3035355a4735425a317074526e526a626d646e57544a6 1633249794e476461534842785a55644e5a316b7a566a42615630316e596c684f4d57517 95a32646156315a6f5a4668765a325674536e4e684d6e4e6e576d3543626d4e595157645 a57454a74576a4a6e5a32517962486c684d30316e596c6857613246755a32645a5748426 f597a4e725a316c59516d356957456c6e59556477626c6c745557646c574842785956637 75a324e496144466b6257396e5a56646f64574a745a326469563342785930646a5a32466 e5054303d

- Modelo: M3 
-  Reflector: ???? 


-  ROT1.: 1 
-  ROT2.: 2 
-  ROT3.: 3 


- POS1.: A 
- POS2.: B 
- POS3.: C 


- ANILLO1: A 
- ANILLO2: B
- ANILLO3: C
- PLUGBOARD: bq cr di ej kw mt os px uz gh 


Para poder resolver el reto debemos, con los datos proporcionados, conocer el texto cifrado que se ha codificado como paso previo en hexadecimal y base64. Es decir, los datos proporcionados se corresponden con la siguiente codificación:
hexadecimal(base64(base64(texto))) 

Mediante consulta online podemos decodificarlo de forma automática.

![image](https://user-images.githubusercontent.com/69391590/123665027-cf6cab00-d82f-11eb-8fc5-cf9536877405.png)

hpsws ksrvp famrx cflon dzjxc cutec msuwh eeauz zblkk fpgqp apfgh wirks mudjx azasy apgmr hjgbd yzjim pxuvj yhnnh mjjpg j


Si vamos a https://cryptii.com/pipes/enigma-machine y aplicamos los valores accedemos al texto en claro original.

![image](https://user-images.githubusercontent.com/69391590/123665305-135fb000-d830-11eb-9294-7e0138b83d43.png)


Ponga atención si fracasamos en esta misión nos veremos abocados a perderlo todo anote esta bandera enigmamtresukwbvi

flag{enigmamtresukwbvi} 

## PISTAS

Pista 1: El nombre del reto hace referencia a una máquina creada durante la segunda guerra mundial.  Antes de nada, lo que se te proporciona es hexadecimal. Conviértelo para conocer el mensaje cifrado real. 

Pista 2: Se utilizó para cifrar mensajes mediante rotores y reflectores aplicando posiciones. Tienes suficientes datos para poder descifrar el mensaje mediante alguna herramienta online. 

Pista 3:   Utiliza https://cryptii.com/pipes/enigmamachine para descifrar el mensaje.

