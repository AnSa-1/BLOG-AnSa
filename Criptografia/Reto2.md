#  reto02 nota_cifrada 

Después de muchos años recopilando documentación, fotos y artículos, se ha decidido realizar una limpieza y llevar la documentación antigua a una nueva sala que le ha cedido el instituto.

En esta sala se pueden archivar de una forma sencilla por fecha todos los documentos del periódico.
Durante este proceso moviendo documentos, una hoja extraña se cae entre los documentos que lleváis. Contiene un texto ilegible junto a la referencia del emperador Julio César. ¿Podrás sacar en claro que quería decir la nota? 

**DATOS**
Yn fvthvragr vasbeznpvba rf pbasvqrapvny. Gr nlhqnen n cebfrthve ra yn vairfgvtnpvba. Ab gr pbasvrf, ab gbqnf ynf vasbeznpvbarf qr ynf dhr qvfcbarzbf fba gna snpvyrf pbzb rfgn ebgnpvba qr pnenpgrerf. Sveznqb: ha nzvtb.   synt{rfgnzbf_rzcrmnaqb_n_pbabpre_nytb_qr_uvfgbevn}

Para poder resolver el reto debemos analizar el texto proporcionado. 
A simple vista cada palabra tiene la misma longitud del texto original y en la última línea parece que tenemos la flag cifrada :
“synt{rfgnzbf_rzcrmnaqb_n_pbabpre_nytb_qr_uvfgbevn}”.

 Existen numerosas herramientas online para solucionar de forma automática el texto cifrado, como CyberChef.  
 
 Si seleccionamos ROT13 desde el menú lateral derecho, realizará la transposición de caracteres y encontraremos la solución.  
 
 Si no tuviéramos conocimiento de estas herramientas online podemos analizar el texto de forma manual aplicando la transposición de caracteres. Escogemos parte de la flag y vamos restando 13 caracteres:  
 
Synt:   
- S-13 = f
- Y-13 = l
- N-13 =a
- Etcétera

![image](https://user-images.githubusercontent.com/69391590/123658684-dbee0500-d829-11eb-99cc-7c4a1087ecfc.png)


## PISTAS

 Pista 1: Los caracteres del texto parecen movidos en el alfabeto. 
 Pista 2: La transposición de caracteres es de 13 caracteres.
 Pista 3: Cifrado clásico César o ROT13. 


