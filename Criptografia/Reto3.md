# reto03 programa_exclusivo

Después de muchos años recopilando documentación, fotos y artículos, se ha decidido realizar una limpieza y llevar la documentación antigua a una nueva sala que le ha cedido el instituto. En esta sala se pueden archivar por fecha de una forma sencilla todos los documentos del periódico.

Al darle la vuelta a la hoja, veis que también tiene otro texto escrito en esa parte, aunque tampoco lo entiendes. Se adjunta también un fichero con extensión pyc. ¿Nos servirá de ayuda? 

¿Podrás proporcionarnos la otra información que está en la otra cara de la hoja?    
  
**DATOS** 

Ax8VCB4HEAAGDDMEBRERPhENAh8DLQQcEQERMAgaBjERAhwEGgADHA==

**DATOS EXTRA**

Os proporcionamos alguna indicación para empezar a resolver el reto: uncompyle6 es una herramienta que descompila el byte-code de Python. Devuelve el fichero original, que necesitarás para resolver la prueba.

Para poder resolver el reto debemos analizar el texto proporcionado y analizar el fichero .pyc para desensamblar su byte-code y convertirlo a su lenguaje, en este caso Python.  
 
Para poder descompilarlo, existen algunos métodos manuales que requieren conocer las cabeceras y versión de este tipo de fichero. En el reto se añade un método directo para descompilar el fichero pyc. El primer paso es abrir un terminal en nuestra Kali desde el directorio /home/incibe/Escritorio/reto03 con el botón derecho y abrir terminal.  Luego tecleamos uncompyle6 xor.pyc y nos mostrará la salida con el código fuente.  
 
Otra alternativa para resolver este reto es hacer uso de pycdc, herramienta similar que producirá la misma salida. 

![image](https://user-images.githubusercontent.com/69391590/123660895-f628e280-d82b-11eb-9f10-bc55f5ec8609.png)

## CODE PYTHON 


```
Python bytecode 2.7 (62211)
Decompiled from: Python 3.8.6 (default, Sep 25 2020, 09:36:53)  
[GCC 10.2.0] 
Embedded file name: xor.py 
Compiled at: 2021-02-01 16:35:44 
import binascii, itertools, base64, sys 
 
  
.    Página 9 de 9 
def xor_crypt_string(data, key='estoesunaclaveparacifrar', encode=False, decode=False): 
    from itertools import izip, cycle 
    import base64 
    if decode: 
        data = base64.decodestring(data) 
    xored = ('').join(chr(ord(x) ^ ord(y)) for x, y in izip(data, cycle(key))) 
    if encode: 
        return base64.encodestring(xored).strip() 
    return xored 
 
 
secret_data = sys.argv[1] 
print 'Cifrado' 
print xor_crypt_string(secret_data, encode=True) 
print 'Descifrado' 
print xor_crypt_string(xor_crypt_string(secret_data, encode=True), decode=True) 
okay decompiling xor.pyc
```

**La función “xor_crypt_string” tiene cuatro argumentos (data, key, encode y decode). Como disponemos explícitamente de la clave y el cifrado xor se emplea en dos direcciones para cifrar y descifrar de igual manera, podemos cambiar el valor decode = True y pasarle el cifrado al programa.**

![image](https://user-images.githubusercontent.com/69391590/123662683-97646880-d82d-11eb-8f5d-ed079b059360.png)

![image](https://user-images.githubusercontent.com/69391590/123662739-a4815780-d82d-11eb-90b5-2da202073a51.png)


 flag{tengo_esta_clave_entre_mis_papeles} 
 

## PISTAS

Pista 1: El fichero pyc es compilado en “byte-code”. Usa uncompyle6 para ver el código fuente del programa. 

Pista 2: Analiza el código fuente. Se realiza un XOR con una clave incluida en el programa. Has de ejecutar el programa con el primer argumento del texto cifrado.  

Pista 3:   Modifica el script para realizar la decodificación  (decode=True en línea 24) y ejecuta python xor.py  Ax8VCB4HEAAGDDMEBRERPhENAh8DLQQcEQERMAga BjERAhwEGgADHA== 
