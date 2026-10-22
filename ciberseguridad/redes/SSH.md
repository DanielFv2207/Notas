# Protocolo Secure Shell (SSH)

Es un método para enviar comandos de forma segura a un ordenador mediante una red no segura. SSH utiliza criptografía para autenticar y encriptar las conexiones entre dispositivos. Se usa normalmente para controlar los servidores a distancia, gestionar
infraestructuras y para transferir datos.
<br>
Cuando viaja, el propietario de una tienda puede dar instrucciones a sus empleados desde lejos para asegurarse de que la tienda opere sin problemas mientras él no está. Del mismo modo, el SSH permite a los administradores gestionar servidores y dispositivos desde lejos.

## ¿Qué hace el SSH?

El SSH permite la conexión entre un usuario y una máquina lejana, puede ser y normalmente son servidores a los que se conectan, este usa una encriptación para codificar los datos que atraviesan la conexión por lo que es bastante
seguro utilizarlo y hace que la desencriptación sea demasiado difícil para los extraños ya que los datos aleatorios no significan nada.
<br><br>
También tiene la capacidad de tunelizar, esto es un método para mover paquetes a través de una red usando un protocolo o ruta que normalmente no podrían utilizar. La tunelización funciona envolviendo paquetes de datos, por lo que todos los datos
que atraviesan una red se dividen en trozos más pequeños y esos trozos se denominan "paquetes".

**SSH se ejecuta sobre el conjunto de protocolo TCP/IP, del que gran parte de Internet depende. El protocolo TCP/IP transporta y entrega paquetes de datos. El uso de TCP es una de las diferencias entre SSH y otros protocolos de tunelización, 
algunos de los cuales utilizan en su lugar el UDP, que es más rápido pero menos fiable.**

## Criptografía de clave pública 

El SSH utiliza una encriptación y autenticación con un proceso llamado criptografía de clave pública, por lo cual es "seguro". La criptografía de clave pública es una forma de encriptación de datos que utiliza dos claves diferentes, la primera es la 
clave pública que utiliza el usuario o cualquiera puede usarla y la otra es la privada que mantiene el propietario en secreto.
<br>
Como estas claves son diferentes porque tienen distintos valores, hacen posible que los dos lados de la conexión negocien claves simétricas o claves idénticas y compartidas para después encriptarlas a través de un canal. una vez que se finaliza la negociación,
las dos partes utilizan claves iguales o simétricas para encriptar todos los datos que se intercambian

## Autenticación

Aunque la criptografía de clave pública autentica los dispositivos conectados en SSH, un ordenador debidamente protegido seguirá requiriendo la autenticación de la persona que utiliza el SSH. A menudo, esto adopta la forma de introducir un nombre de usuario y
una contraseña.
<br>
Una vez completada la autenticación, la persona puede ejecutar los comandos en la máquina remota, como si lo estuviera haciendo en su propia máquina local.

## Tunelización o reenvío de puertos

El reenvío de puertos envía paquetes de datos dirigidos de una dirección IP y a un puerto de una máquina a una dirección IP y a un puerto de una máquina diferente.
<br>
Por ejemplo para entenderlo fácilmente, si un administrador quiere realizar cambios en un servidor pero se encuentra en otro lugar por lo que debe hacerlo de forma remota, el servidor se encuentra en una red privada, pero ese servidor solo recibe paquetes 
de datos de otros computadores que se encuentran dentro de la red privada, el administrador lo que puede hacer es conectarse a un segundo servidor que se encuentre dentro de la red y que se encuentre abierto recibir tráfico de internet, después utiliza el reenvío de
puertos SSH para conectarse al primer servidor. Desde la perspectiva del primer servidor, los paquetes de datos del administrador se originan en el interior de la red privada.

## ¿Qué puerto es SSH?

El puerto 22 es el puerto por defecto para el SSH. A veces, los firewalls pueden bloquear el acceso a determinados puertos en los servidores detrás del firewall, pero dejar abierto el puerto 22. 
Por lo tanto, el SSH es útil para acceder a los servidores situados al otro lado del firewall: los paquetes dirigidos al puerto 22 no se bloquean y pueden reenviarse a cualquier otro puerto.


