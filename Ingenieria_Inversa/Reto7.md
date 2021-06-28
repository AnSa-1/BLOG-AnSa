# reto07 Crackme 

En el escritorio del usuario de uno de los ordenadores localizáis una aplicación. Os aseguráis de que no sea maliciosa y ejecutáis el fichero exe. Parece contener dos entradas de texto. 

Pregunta:

Hay dos flags en esta prueba, recupera la flag1 del fichero exe.

**DATOS**

Fichero ejecutable. 

Abrimos el fichero .exe con dnSpy en Windows. Para ello lo arrastramos al área de trabajo.

![image](https://user-images.githubusercontent.com/69391590/123679111-0c8c6980-d83f-11eb-8825-f23a3b0cf4f2.png)

Si navegamos por el árbol de objetos, encontramos un “namespace CrackMeEasy” dentro de Form1. Nos piden la flag1 que se corresponde con la acción asociada al botón “btnActivate_Click”. Este método privado tiene el siguiente código.  
 
 
 ```private void btnActivate_Click(object sender, EventArgs e)
   {    
	string inputString = 
XOREncryption.Base64Decode("AAICBBIOCQASCAUOAg4PAgQFCAUO");    
		if (this.serialNumber.Text == 
XOREncryption.encryptDecrypt(inputString)) 
		 {
			MessageBox.Show("Correcto ! Introduce la flag1 así:
 flag{password}");
		        return;
                        }
			MessageBox.Show("Error !", "Info");   
		}
```

Es decir, si introducimos correctamente la cadena correspondiente a decodificar inputString, tendremos la flag1. Necesitamos conocer con que clave ha sido codificado. Para ello, pichamos sobre la rutina “XOREncryption.encryptDecrypt” para conocer dicha clave.

![image](https://user-images.githubusercontent.com/69391590/123679954-064abd00-d840-11eb-84c6-e2fe7927e9eb.png)


Ya tenemos todos los elementos para conocer la flag. Vamos a CyberChef a introducir los datos. 

Como la cadena ha sido previamente codificada a base64, aplicamos primero “From Base64” y después XOR y clave ‘A’. 

![image](https://user-images.githubusercontent.com/69391590/123680062-2a0e0300-d840-11eb-872c-afa99504af76.png)


Tenemos la palabra de paso “ACCESOHASIDOCONCEDIDO”. Probamos a introducirla en el programa. 

![image](https://user-images.githubusercontent.com/69391590/123680138-427e1d80-d840-11eb-8926-f297df94925e.png)


flag{ACCESOHASIDOCONCEDIDO} 

## PISTAS

 Pista 1: El binario se puede comprobar con file. Es un fichero “PE32+ executable (GUI) x86-64 Mono/.Net assembly, for MS Windows”. 
 
Pista 2: Se puede descompilar con dnSpy para leer el código fuente. En el existen las rutinas que deberás analizar. Para la flag1 la rutina es XOREncryption con clave ‘A’

 Pista 3:   El cifrado se corresponde a un XOR con calve ‘A’ de “AAICBBIOCQASCAUOAg4PAgQFCAUO”.


    
    
    
    
   
