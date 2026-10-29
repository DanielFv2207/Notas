# Procesos en Linux

Toda tarea que se ejecuta dentro de un sistema se le llama *proceso* por lo que al Linux ser un sistema multiusuario, si cinco usuarios están ejecutando un mismo programa desde cinco equipos diferentes, habrá cinco procesos distintos.

Los procesos hacen uso del CPU para realizar sus instrucciones y cada proceso tiene sus propios derechos y responsabilidades. El recurso más valioso de un sistema es la CPU y si hay más procesos que CPUs estos deben esperar en memoria a que le sea asignado tiempo de computación.
Linux trata de maximizar su uso de la forma más eficiente a través del control de procesos.

Más adelante vamos a ver algunos comandos para controlar los procesos y los recursos que utilizan los procesos.

## Características 

### 1. Propiedades

Un proceso incluye, no sólo el programa que ejecuta, sino toda la información necesaria para diferenciar una ejecución del programa de otra.

#### Identificadores:

**PID(Process ID):** número de referencia único que tiene cada proceso que se inicia. Lo genera el Kernel. <br>
**UID, GID (User ID, Group ID):** usuario y grupo al que pertenece el proceso. Estas determinan los derechos del proceso a acceder a los recursos del sistema y ficheros. <br>
**PPID(Parent Process ID):** PID del proceso padre. <br>

### 2. Estados de un proceso

Cuando un proceso se ejecuta su estado cambia debido a sus circunstancias:

<img width="493" height="257" alt="image" src="https://github.com/user-attachments/assets/3d531003-7a0b-4329-9f28-9e383b3cc561" />

**Running:** el proceso se está ejecutando o está listo para ello (esperando a que se le asigne tiempo de CPU) <br>
**Waiting:** el proceso está esperando un evento o recurso. Linux diferencia entre interrumpible e ininterrumpible. Mientras el primero puede detenerse mediante una señal los segundos están esperando a una condición del hardware y no puede ser
detenido por ninguna circunstancia. <br>
**Stopped:** el proceso está detenido, usualmente debido a recibir una señal. <br>
**Zombie:** es un proceso que ha completado su ejecución pero aún tiene una entrada en la tabla de procesos, permitiendo al proceso que lo ha creado leer el estado de su salida.

### 3. Concurrencia

A la capacidad de ejecutar varios procesos de forma simultánea se le llama concurrencia. Si realmente hay varios a la vez se le llama paralelismo, este se genera ya que el sistema operativo comparte los recursos.
Los procesos pueden ser concurrentes si pueden ejecutarse en paralelo o secuenciales si se ejecutan uno después de otro (mediante waitpid o mediante eventos).

### 4. Servicios y funcionalidad

Linux nos ofrece un conjunto de funciones o llamadas al sistema para la gestión de procesos:

Creación planificación eliminación de procesos, bloquear y desbloquear procesos, mecanismos de sincronización, mecanismos de comunicación

### 5. Creación de procesos

<img width="466" height="287" alt="image" src="https://github.com/user-attachments/assets/9e5da0ef-4da8-4a1c-b3b9-ed926fdb12f8" />

En Linux se crea un nuevo proceso con la llamada al sistema (fork) del proceso padre. El proceso hijo hereda algunos aspectos del padre (espacio de direcciones lógico, tabla de programación de señales, los dispositivos cirtuales,
el usuario/grupo y las variables de entorno). No hereda los identificadores, los contadores internos de utilización y las alarmas y señales pendientes.

### 6. Comunicación entre procesos

**A través de variables de entorno:** solo es posible de padres a hijos. <br>
**Mediante una señal:** solo indica que algo ha ocurrido y solo lleva como información de un número de señal. <br>
**Mediante entrada-salida:** es la forma más corriente a nivel de shell. Ejemplo: el operador pipe "|" que conecta dos procesos. <br>
**Mediante técnicas IPC u otras:** semáforos, memoria compartida, colas de mensajes.

## Comandos

### 1. Monitorización de procesos

*$PS*

Sintaxis:    ps [opciones] <br>
Muestra la lista de procesos del sistema y algunas de sus características: hora de inicio, uso de memoria, estado de ejecución, propietario y otros detalles. <br>

Opciones: <br>
-a    Muestra los procesos creados por cualquier usuario y asociados a un terminal <br>
-l    Formato largo. Muestra prioridad, el PID del proceso padre <br>
-u    Formato de usuario. Incluye el usuario propietario del proceso y la hora de inicio <br>
-U     usr lista los procesos creados por el usuario “usr” <br>
-x    Muestra los procesos que no están asociados a ningún terminal del usuario (entre ellos los “daemons”)

*$PSTREE*













