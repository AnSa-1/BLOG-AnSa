# reto24 gana en la ruleta

En clase de lengua se ha estudiado la táctica a seguir para optimizar juegos del tipo de la ruleta de la fortuna.

¿ Podrás aplicar esos conocimientos al siguiente texto para encontrar el mensaje oculto? 

**DATOS**

text.txt

Para resolver este reto hay que analizar el texto entregado. Se trata de un texto que no se puede leer, en el que al final de este aparece algo identificable:

```dxrj{rmrxisrmfv_xr_dbpnepmnir_pm_em_ypkyv}```

Parece que aquí está oculta la flag, por lo que puede tratarse de un problema de criptografía por sustitución de caracteres, siendo los primeros cuatro.

- D - F 
- X - L
- R - A 
- J - G

Para averiguar el resto de los caracteres habría que realizar un análisis de la frecuencia de estos, por ejemplo en

https://www.cryptool.org/en/cto/cryptanalysis/frequency-analysis 

![image](https://user-images.githubusercontent.com/69391590/124317419-0d8b0700-db6f-11eb-8ffb-10f5b35d6569.png)

Se consulta cual es la frecuencia de repetición en el lenguaje español, por ejemplo aquí:

https://www.sttmedia.com/characterfrequency-spanish

Y se van sustituyendo los caracteres Alguno puede varia con respecto a la frecuencia habitual, aunque los principales coinciden y a partir de estos y del texto (que es un trozo de El Quijote) es fácil obtener todo el alfabeto

El alfabeto sustituido se corresponde con: ```ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz``` ```RTNFPDJZIWOXUMVQABHYEGLKCSrtnfpdjziwoxumvqabhyeglkcs```

La flag sería flag{analizando_la_frecuencia_en_un_texto} 

## PISTAS

 Pista 1: Identifica donde está la flag gracias a “{“ y “}“ 
 
 Pista 2: Sustituye los caracteres que preceden a { por flag
 
  Pista 3: Realiza un análisis de la frecuencia del resto de caracteres
