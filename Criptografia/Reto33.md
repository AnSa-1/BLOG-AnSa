# reto33_EnglishBreakFast

Hoy es el día de visita al museo. Estáis todos esperando a entrar.

Te das cuenta de que la entrada al museo tiene un mensaje en el reverso "Descifra el mensaje.". Lo firma Mr.EnglishBreakFast. 

Pregunta ¿Qué mensaje ha transmitido Mr.EnglishBreakFast? 

**DATOS**

fichero txt.

```wp𝐡𝐊lw𝐈b𝐬𝐨k𝐁UjJ𝐝gw𝐋hsK𝐇𝐐𝐜MqsR𝐯cKxceUbi𝐣Rm𝐬𝐖𝐰kl𝐌𝐎f𝐀```

El nombre de la tarea y también el hecho de que tengamos diferentes tipos de letra, hacen pensar en el cifrado del bacon. 

![image](https://user-images.githubusercontent.com/69391590/124357904-c015a500-dc15-11eb-9ed9-16d7d22b7234.png)


El primer paso obvio es decodificar el cifrado de bacon para el caso de diferentes tipos de letra. Si lo decodificamos en notación A (normal)/B (negrita) según la que se suele utilizar obtenemos lo siguiente:

```AABBA ABABB ABAAA BAABA AABBB AAAAB AAAAA AAABA ABBBA ABBAB ```

``` g     l     i    s     h     b    a      c     o     n ```
  
  Esto parece una parte del texto plano. Pero, el texto también utiliza mayúsculas y minúsculas, que también es una forma conocida de codificar datos como cifrado bacon. Descodificando a partir de esta idea (minúsculas - A, mayúsculas - B), obtenemos lo siguiente:
  
 ``` AAABA ABAAA ABBAB AAABA ABBBA BAABA ABAAA BAAAB AABAA ABBAB```
 
 ```c  i  n  c  o  s  i  r  e  n ```
 
 Otra forma de codificar los datos en este tipo de cifrado se basa en la posición de la letra en el alfabeto. Si está en posiciones impares - A, si está en posiciones pares - B. La decodificación produce lo siguiente: 
 
 ```ABBAB AABAA ABABB BAABB AABAA AAABB AABAA ABABB AAAAA BAABA ```
 
``` n e l t e  d e  l a s``` 

 Para obtener la última parte, podemos utilizar de nuevo el cifrado basado en la posición de los caracteres. Si se trata de las primeras 13 letras - A, de lo contrario - B: 
 
 ```BBAAA BAABB AABAA AABAA BAABA ABBBB AABAA BAAAB ABBBA AABAA ```
 
```y t e e s p e r o e ```

Con estos cuatro pasos obtenemos la flag{yteesperoeneltedelascincosirenglishbacon}

## Script en Python: 

```bacon.py
# coding=utf-8 
import codecs 
import string 
 
tbl = { 
    "AAAAA": "a", 
    "AAAAB": "b", 
    "AAABA": "c", 
    "AAABB": "d", 
    "AABAA": "e", 
    "AABAB": "f", 
    "AABBA": "g", 
    "AABBB": "h", 
    "ABAAA": "i", 
    "ABAAB": "j", 
    "ABABA": "k", 
    "ABABB": "l", 
    "ABBAA": "m", 
    "ABBAB": "n", 
    "ABBBA": "o", 
    "ABBBB": "p", 
    "BAAAA": "q", 
    "BAAAB": "r", 
    "BAABA": "s", 
    "BAABB": "t", 
    "BABAA": "u", 
    "BABAB": "v", 
    "BABBA": "w", 
    "BABBB": "x", 
    "BBAAA": "y", 
    "BBAAB": "z" 
} 
 
 
def decode_bacon(dt): 

 splt = [dt[i:i + 5] for i in range(0, len(dt), 5)] 
    cc = "" 
    for ss in splt: 
        print ss 
        cc += tbl[ss] 
    print cc 
    return cc 
 
 
d = codecs.open("english_breakfast.txt", "rb", encoding='utf-8').read() 
caps = u"𝐚𝐛𝐜𝐝𝐞𝐟𝐠𝐡𝐢𝐣𝐤𝐥𝐦𝐧𝐨𝐩𝐪𝐫𝐬𝐭𝐮𝐯𝐰𝐱𝐲𝐳𝐀𝐁𝐂𝐃𝐄𝐅𝐆𝐇𝐈𝐉𝐊𝐋𝐌𝐍𝐎𝐏𝐐𝐑𝐒𝐓𝐔𝐕𝐖𝐗𝐘𝐙" 
norm = string.ascii_lowercase + string.ascii_uppercase 
 
p4 = "" 
unpart4 = "" 
for i in d: 
    c = i 
    ii = caps.find(i) 
    if ii != -1: 
        p4 += 'B' 
        c = norm[ii] 
    else: 
        p4 += 'A' 
 
    unpart4 += c 
 
p3 = "" 
unpart3 = "" 
for i in unpart4: 
    c = i 
    if c in string.ascii_uppercase: 
        p3 += 'B' 
        c = string.lower(c)
           else: 
        p3 += 'A' 
 
    unpart3 += c 
 
p2 = "" 
for i in unpart3: 
    if (ord(i) - ord('a')) % 2 == 0: 
        p2 += 'A' 
    else: 
        p2 += 'B' 
 
p1 = "" 
for i in unpart3: 
    if (ord(i) - ord('a')) < 13: 
        p1 += 'A' 
    else: 
        p1 += 'B' 
 
print decode_bacon(p1) + decode_bacon(p2) + decode_bacon(p3) + decode_bacon(p4)
```

![image](https://user-images.githubusercontent.com/69391590/124358467-5945bb00-dc18-11eb-8a19-42ea956652b1.png)

## PISTAS

Pista 1: Cifrado bacon

 Pista 2: Hay 4 patrones para emplear el mismo cifrado bacon. Siendo A en un caso B en otro. 
 
 Pista 3: Los patrones son: diferentes tipos de letra, mayúsculas y minúsculas y posición de letras par o impar o a partir de cierto número

