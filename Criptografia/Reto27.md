# reto27 MultiCrypto 


Hoy tenemos un examen de matemáticas, concretamente del temario de criptografía y codificación de mensajes. El examen consiste en descifrar el mensaje ocult

Pregunta: ¿Serás capaz de aprobar? 

**DATOS**

Fichero de texto. 

Descargamos el fichero reto27.txt y vemos el contenido

```reto27.txt 
Vxoskx tobkr jk iolxgju_OPACQ3XGTHYCM2JVLWWM65JYT4WM42RCSBCIG3RHUTVW====KA2ZYPPCMKYZKS HLM4FYQTZMKA3MMPPCSEYZKSHLM4EYQTFBKA3JQPPCMWYZSSPLMOEIQTFBKA3MQPPCSEYZ QFW=KA3JSPPCSSYZSSPLME3YQT3IKA2JUPPAMSYZOTFLMWFYQTHZKA2JIPPAMKYZOSPLMW 3YQTHXKA2JMPPBMWYZQTHLMA2IQTHZKA2ZOPPBMWYZOTFLMWFYQTPAKA2JIPPAMSYZOSPL MWFYQTHZKA2JUPPAMKYZOSPLMA2IQTPAKA2JMPPAMKYZQTHLMA2IQTPAKA2JM===KA3AO===```




Podemos observar un mensaje codificado. En los primeros caracteres aparecen espacios en blanco lo que nos puede inducir a pensar que son palabras y que pueden estar cifradas con el algoritmo del Cesar. Intentamos descifrar toda la cadena con tdas las posibles claves y con la clave igual a 6 obtenemos el siguiente texto 

 (https://cryptii.com/pipes/caesarcipher)


 ![image](https://user-images.githubusercontent.com/69391590/124318017-f26cc700-db6f-11eb-97df-74a285321f51.png)

 
 ```Primer nivel de cifrado_IJUWK3RANBSWG2DPFQQG65DSN4QG42LWMVWCA3LBONPQ====EU2TSJJWGESTEM BFG4ZSKNTGEU3GGJJWMYSTEMBFG4YSKNZVEU3DKJJWGQSTMMJFGIYCKNZVEU3GKJJWMYST KZQ=EU3DMJJWMMSTMMJFGY3SKN3CEU2DOJJUGMSTINZFGQZSKNBTEU2DCJJUGESTIMJFGQ 3SKNBREU2DGJJVGQSTKNBFGU2CKNBTEU2TIJJVGQSTINZFGQZSKNJUEU2DCJJUGMSTIMJF GQZSKNBTEU2DOJJUGESTIMJFGU2CKNJUEU2DGJJUGESTKNBFGU2CKNJUEU2DG===EU3UI= == ```
 
 En la cadena resultante vemos unos primeros caracteres que nos muestra la frase “Primer nivel de cifrado_” loo que nos induce a pensar que los siguientes caracteres están cifrados/codificados con otro algoritmo. Por el formato parece base32 o base64, si decodificamos la cadena en base32 obtenemos el siguiente resultado: 
 
 ``` base32 -d base32_data.txt > base32_decoded.txt ```
 ```cat base32_decoded.txt 
 Bien hecho, otro nivel mas_%59%61%20%73%6f%6c%6f%20%71%75%65%64%61%20%75%6e%6f%5f%66%6c%61%67 %7b%47%43%47%43%43%41%41%41%47%41%43%54%54%54%43%54%54%47%43%54%41%43% 41%43%43%47%41%41%54%54%43%41%54%54%54%43%7D ```
 
 Obtenemos la cadena en claro “Bien hecho, otro nivel más”. El resto de la cadena parece estar codificado con URLencode, por lo que aplicando el algoritmo de descifrado obtenemos  (https://www.urldecoder.org/): 

![image](https://user-images.githubusercontent.com/69391590/124318252-437cbb00-db70-11eb-92fd-309c980547fc.png)

``` Ya solo queda uno_flag{GCGCCAAAGACTTTCTTGCTACACCGAATTCATTTC} ```

Como indica el mensaje, parece que el contenido de la flag es “GCGCCAAAGACTTTCTTGCTACACCGAATTCATTTC”. 

Si analizamos la cadena de caracteres está formada por las siguientes letras: “GCAT”, que coincide con las letras de las proteínas que forman el ADN (G:Guanina, C: Citosina, A:Adenina y T:Timina), por lo que podemos deducir que está cifrado con DNA Cypher. Con el siguiente script intentams descifrar el contenido:

```  dnadecode.py
mapping = { 
'AAA':'a', 
'AAC':'b', 
'AAG':'c', 
'AAT':'d', 
'ACA':'e', 
'ACC':'f',  
'ACG':'g', 
'ACT':'h', 
'AGA':'i', 
'AGC':'j', 
'AGG':'k', 
'AGT':'l', 
'ATA':'m', 
'ATC':'n', 
'ATG':'o', 
'ATT':'p', 
'CAA':'q', 
'CAC':'r', 
'CAG':'s', 
'CAT':'t', 
'CCA':'u', 
'CCC':'v', 
'CCG':'w', 
'CCT':'x', 
'CGA':'y', 
'CGC':'z', 
'CGG':'A',
'CGT':'B', 
'CTA':'C', 
'CTC':'D', 
'CTG':'E', 
'CTT':'F', 
'GAA':'G', 
'GAC':'H', 
'GAG':'I', 
'GAT':'J', 
'GCA':'K', 
'GCC':'L', 
'GCG':'M', 
'GCT':'N', 
'GGA':'O', 
'GGC':'P', 
'GGG':'Q', 
'GGT':'R', 
'GTA':'S', 
'GTC':'T', 
'GTG':'U', 
'GTT':'V', 
'TAA':'W', 
'TAC':'X', 
'TAG':'Y', 
'TAT':'Z', 
'TCA':'1', 
'TCC':'2', 
'TCG':'3', 
'TCT':'4', 
'TGA':'5', 
'TGC':'6', 
'TGG':'7', 
'TGT':'8', 
'TTA':'9', 
'TTC':'0', 
'TTG':' ', 
'TTT':'.' 
} 
string = 'your_strings' 
def decode_dna( string ): 
    pieces = [] 
    for i in range( 0, len(string), 3 ): 
        piece =  string[i:i+3] 
        # pieces.append() 
        pieces.append( mapping[piece] ) 
    return "".join(pieces) 
print decode_dna(string) ```

Lo ejecutamos: 
``` python2 dnacode.py
Much0 Crypt0 ```

Con este texto reconstruimos la flag: flag{Much0 Crypt0} 

## PISTAS

 
 Pista 1: Criptografía tradicional: Cesar
 
 Pista 2: Prueba diferentes algoritmos de codificación,no siempre es base64 
 
 Pista 3: La solución está en los genes
 
 
