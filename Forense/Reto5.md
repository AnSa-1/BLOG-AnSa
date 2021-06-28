# reto05 exfiltración

Hablais con el director del instituto y os permite acceder al contenido del disco. Al entrar encontráis un pcap. ¿Qué es un pcap? os preguntáis. No lo sabemos, pero habrá que investigar. 

Los datos os suenan codificados en hexadecimal, pero ... ¿Cómo recomponer estas piezas de cada petición? Además, hay mucho ruido de navegación en el fichero.

**DATOS**

Fichero “pcap” descargable.

Abrimos el fichero pcap con Wireshark. Identificamos que ha sido capturado a nivel de protocolo. Para ello, accedemos a  **Estadísticas  ->  Jerarquía de Protocolo **

![image](https://user-images.githubusercontent.com/69391590/123674902-0d6ecc80-d83a-11eb-9e10-a2a52d96c9c4.png)

En la ventana de estadísticas vamos a aplicar un filtro sobre el protocolo DNS.

![image](https://user-images.githubusercontent.com/69391590/123674989-25dee700-d83a-11eb-93a8-7886e7d0fef6.png)


Al final de todo el tráfico vamos a encontrar consultas que no se pueden resolver a algunos subdominios. Deberemos concatenar dichas consultas y convertirlas a texto claro, ya que es el texto que se está exfiltrando. 


![image](https://user-images.githubusercontent.com/69391590/123675104-427b1f00-d83a-11eb-9f26-5b994fafd866.png)


Las incluimos en un texto “exfilpass.hex” cuyo contenido es el siguiente.  

- 45737465206669636865726f206573206d757920696d706f7274616e7465 
- 2e20446573747275697220756e612076657a206c6569646f2e204e6f2074 
- 69656e652073656e7469646f20717565206f74726f73206f6a6f73207175 
- 65206e6f207365616e206c6f73207475796f73206c6f207665616e2e200a 
- 4c65616e202c207665616e20c2bf517565206d61732064613f0a0a666c61 
- 677b646e735f7370795f657866696c74726174696f6e7d200a0a 

Mediante un bucle recorremos el fichero en bash y convertimos de hexadecimal a string con xxd.  

```for sub in `cat exfilpass.hex`; do echo $sub | xxd -r -p; done```

Recuperamos el texto original que fue transmitido en la red a través de consultas erróneas DNS. 


![image](https://user-images.githubusercontent.com/69391590/123675671-e95fbb00-d83a-11eb-8e1d-e1578157ee8e.png)


 flag{dns_spy_exfiltration} 
 
 
## PISTAS

Pista 1: Utiliza Wireshark para abrir el fichero. Mira en Estadísticas->Jerarquía de Protocolo. 

Pista 2: Filtra por consultas al “Domain Name System” (DNS) y observa las consultas fallidas. 

Pista 3:   Pasa de hexadecimal a “string” el contenido de las consultas a los subdominios (parte hexadecimal).
