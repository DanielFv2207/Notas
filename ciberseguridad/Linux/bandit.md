# Niveles de Bandit OverTheWire

## Nivel 0

Para este nivel lo que me piden es logearme en el juego haciendo uso de SSH, para esto primero tuve que investigar sobre qué era y para que servía SSH, por lo que leí y tome algunas [notas](https://github.com/DanielFv2207/Notas/blob/main/ciberseguridad/redes/SSH.md).
Después, lo que hice fue que en mi máquina virtual de Ubuntu y por la terminal ingresé los comandos para conectarme correctamente con los datos que nos da la página: 

**URL:** bandit.labs.overthewire <br>
**Port:** 2220 <br>
**Username:** bandit0 <br>
**Password:** bandit0 <br>

Para logearme correctamente hice uso del comando: *ssh -p 2220 bandit0@bandit.labs.overthewire.org* utilicé el -p para especificar el puerto donde debo ingresar ya que el que viene por defecto en SSH no me sirve.

<img width="418" height="153" alt="image" src="https://github.com/user-attachments/assets/74382b62-a4bf-452b-b00c-14f3803b2648" />

Una vez hecho esto, el sistema me pide la contraseña por lo que ingreso la contraseña que me dieron e ingreso al sistema.

## Nivel 1

Para este nivel me dice que debo encontrar la contraseña para pasar al siguiente nivel y la puedo encontrar en un archivo llamado *readme* por lo que primero usando **ls** miro los archivos existentes y después usando **cat** miro el contenido que tiene 
el archivo *readme*:

<img width="485" height="147" alt="image" src="https://github.com/user-attachments/assets/c0c70e26-c808-47fa-a086-89cf96c3c1f0" />

La contraseña para pasar al nivel 2 es: 6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR

## Nivel 2

Para este nivel me deslogeo del bandit0 en el que me encuentro y para entrar al siguiente uso otra vez ssh pero ahora con
usuario **bandit1** y así voy a hacer de ahora en adelante para ingresar a los siguientes niveles. Este nivel me dice que 
para pasar al siguiente debo buscar la contraseña que se encuentra en el archivo llamado "-".

<br>
Para ver el contenido que hay en este archivo lo que se hace es utilizar *cat ./-* esto se hace ya que el guion lo toma como
un carácter especial y no se puede hacer de forma normal, para todos los archivos que inician por guion puedo usar este mismo método.
<br>
<img width="220" height="49" alt="image" src="https://github.com/user-attachments/assets/32c8931a-bce4-4af0-bc83-a49e0a4eea94" />

La contraseña para pasar al nivel 3 es: PK8fYLZg2hnHSz83plBL1iEPKdD3QToB

## Nivel 3

Este nivel me pide buscar la contraseña que se encuentra guardada en el archivo llamado: *--spaces in this filename--* por lo que hago para ver lo que hay en este archivo es poner todo el nombre del archivo dentro de comillas dobles, hago esto siempre que tenga un archivo con espacios en el nombre aparte también hago uso de **./** ya que el nombre incia por un guion.

<img width="219" height="32" alt="image" src="https://github.com/user-attachments/assets/faf984f9-555d-4e01-a768-e2565f4817b7" />

La contraseña para pasar al nivel 4 es: 7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME

## Nivel 4

Este nivel me pide que encuentre la contraseña que está almacenada en un archivo oculto en la carpeta **inhere**.
Primero lo que hago es meterme a la carpeta inhere y haciendo uso del comando *find* puedo buscar todos los arvhivos y directorios que se encuentran dentro de esta carpeta. Después de esto simplemente haciendo uso de *cat* busco la contraseña que necesito.

<img width="236" height="122" alt="image" src="https://github.com/user-attachments/assets/82955a63-e851-46a4-bb37-5c35a2c73b75" />

La contraseña para pasar al nivel 5 es: xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq

## Nivel 5

Este nivel me dice que la contraseña para pasar al siguiente se encuentra en un archivo el cual solo un humano puede leerlo dentro de la carpeta llamada *inhere* lo que yo hice para resolverlo es primero ver el contenido que había en la carpeta inhere usando el comando find y después con **cat** busqué archivo por archivo cual era el que contenía la contraseña que se puede leer solo por una persona.

<img width="430" height="356" alt="image" src="https://github.com/user-attachments/assets/adc73282-a521-4248-9261-2a93658b78dd" />

La contraseña para pasar al siguiente nivel es: 6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG

## Nivel 6

Para este nivel me dice que la contraseña se encuentra en algún lugar en la carpeta inhere y tiene las siguientes propiedades: 
<br>

human-readable <br>
1033 bytes in size <br>
not executable <br>

Para resolver esto la forma más fácil es buscar la carpeta que tenga el tamaño exacto de 1033 bytes haciendo uso de find -size, el punto después del find es para que busque en todos los archivos de la carpeta actual.

<img width="320" height="92" alt="image" src="https://github.com/user-attachments/assets/bfba8dea-2888-4d7f-8e74-a9283344be0c" />

La contraseña para pasar al siguiente nivel es: pXa26xhMWaC2SvDotA4r9EgZkulOeSBW

## Nivel 7

Este nivel me dice que la contraseña se encuentra almacenada en algún lugar del servidor con las siguientes propiedades: 

owned by user bandit7 <br>
owned by group bandit6 <br>
33 bytes in size <br>

En este caso lo que puedo hacer para buscarlo seria usar *find* con cada una de las propiedades que me dieron pero si lo hago solo con ese comando no me va a dejar ya que el sistema me mostrará mensajes de error ya que no cuento con permisos, por lo que ingresando al final *2>/dev/null* puedo ejecutar el comando y esconder estos mensajes de error.

<img width="310" height="50" alt="image" src="https://github.com/user-attachments/assets/d5af4758-0dbb-4d8a-a754-3dc54a0b2a19" />

La contraseña para pasar al siguiente nivel es: Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3

## Nivel 8

Este nivel me dice que la contraseña se encuentra en un archivo llamado **data.txt** siguiente a la palabra "millionth"

Para resolver este nivel puedo hace ruso del *grep* ya que me ayuda a encontrar palabras que se encuentren dentro de los archivos

<img width="206" height="20" alt="image" src="https://github.com/user-attachments/assets/a7cd7392-3121-4c19-9d30-37e11ab66918" />

La contraseña para pasar al siguiente nivel es: VR1ljMayciFxbnUokuQmJFw6QC9VKtub

## Nivel 9

La contraseña para el siguiente nivel se encuentra en el archivo data.txt y es la única línea de texto que aparece una sola vez.











