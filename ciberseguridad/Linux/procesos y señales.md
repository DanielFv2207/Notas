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

Sintaxis: pstree [opciones] [PID] [user] <br>
Este comando muestra la jerarquía de los procesos mediante una estructura en árbol. Si se especifica un PID de proceso mostrará a partir de este, 
de lo contrario comienza por el proceso init (PID=1) y mostrará todos los procesos del sistema. Si se especifica un usuario válido se mostrará la jerarquía de todos los procesos del usuario.

Opciones: <br>
-a    Incluye en el árbol de procesos la línea de comandos que se usó para iniciar el proceso. <br>
-c    Deshabilita la unión de procesos hijos con el mismo nombre (replicas de un mismo proceso) <br>
-G    Usa los caracteres de línea para dibujar el árbol. La representación el árbol es mas clara. <br>
-h    Remarca la jerarquía del proceso actual. <br>
-n    Por defecto los procesos con mismo padre se ordenan por el nombre. Esta opción fuerza a ordenar los procesos por su PID <br>
-p    Incluye el PID de los procesos en el árbol 

*$TOP*

Sintasix: top [opciones] <br>
El comando TOP ofrece una lista de procesos similar al comando ps, pero la salida se actualiza continuamente, especialmente útil cuando es necesario observar el estado de los procesos o comprobar los recursos que consumen.

Opciones: <br>
-i Ignora a los procesos inactivos listando únicamente los que utilizan recursos del sistema. <br>
-d Especifica el ritmo de actualización de la pantalla en segundos. Es posible especificar decimales. <br>

Ordenes: <br>
h    Muestra una pantalla de ayuda <br>
q    Sale del programación <br>
k    Kill. Permite detener un procesos <br>
r    Renice. Permite alterar la prioridad de un proceso


*$HTOP*

De funcionamiento similiar a TOP el comando HTOP ofrece algunas ventajas como la navegación entre procesos, tanto vertical como horizontalmente mediante las flechas en el teclado, una mejora visual con el añadido de los medidores de consumo de la CPU y una barra inferior con opciones (F1-F10) que permiten entre otras cosas filtrar la información o matar un proceso situándonos sobre el.

Opciones <br>
-s    Ordena por columna  <br>
-u    Muestra solo los procesos de un usuario <br>
-p    Muestra solo la informacion de los PIDs introducidos <br>

### 2. Ejecución en primer y segundo plano

Para ejecutar un proceso en primer plano solo se hace introduciendo el nombre en la terminal y pulsando intro. Con un proceso en primer plano se pueden hacer dos acciones: Matar el proceso con Ctrl-c, hace que se cancele el proceso y se librean los recursos
asignados. Parar el proceso con Ctrl-z, en este caso sólo se detiene su ejecución, conservando su estado y recursos para poder continuar en el momento que se da la orden "fg".

Un proceso ejecutado en segundo plano no bloquea la terminal desde el que se lanzó. Los programas pueden iniciarse en segundo plano añadiendo el carácter *&* al final del comando. Cuando un proceso se ejecuta en segundo plano se crea un trbajo (job)
al cual se le asigna un número entero empezando por 1 y numerado secuencialmente. La única manera de comunicarse con el proceso es mediante mensajes (signals). Se puede mover un programa ejecutando en primer plano al segundo plano deteniéndolo usando
Ctrl+z y después reiniciándolo en segundo plano mediante la orden "bg".

### 3. Señales a procesos

Cada proceso que se ejecuta en el sistema está alerta de los mensajes enviados por el kernel o el usuario. Se usan los comando kill y killall para enviar estas señales. Existen 30 señales diferentes definidas en Linux, cada una de ellas tiene un nombre y un entero 
asociado.

<img width="476" height="260" alt="image" src="https://github.com/user-attachments/assets/f16b37ca-8b36-47e5-9a24-c72762101e4b" />


*$KILL*

Sintaxis: kill [-s sigspec | -sigspec] [pids] <br>
El comando kill permite enviar un mensaje a un proceso o varios por sus números PID. El parámetro sigspec es el valor entero de la señal que enviaremos al proceso. Si se omite sigspec en el comando kill se toma por defecto el valor SIGTERM (15, salir de manera correcta).

Ejemplos (comandos equivalentes): <br>
$kill 4515            kill -s TERM 4515 <br>
$kill -SIGTERM 4515    kill -s 15 4515 <br>
$kill -s 15 4515        kill -s sigterm 4515

*$KILLALL*

Sintaxis: killall [-s sigspec | -sigspec ] nombreproceso <br>
Esta orden es ligeramente diferente a kill, en primer lugar utiliza el nombre de proceso en lugar del PID y además envía la señal a todos los procesos con el mismo nombre. Por lo demás su comportamiento es idéntico a kill

### Control de procesos desde el terminal

Cuando lanzamos un proceso en segundo plano obtenemos un PID y un número de trabajo. A diferencia del PID (único) el número de trabajo es un identificador de uno o varios procesos correspondientes a un usuario.

*$JOBS* 

Sintaxis: jobs [options] [jobspec] <br>
Lista todas las tareas activas. Si se incluye jobspec únicamente listará la información sobre esas tareas.
Con la orden jobs podemos obtener una lista de los trabajos que hemos lanzado en el sistema.

Opciones: <br>
-l Lista los PID de las tareas

*$FG (foreground)*

Sintaxix: fg [jobspec] <br>

Se utiliza para traer a primer plano un trabajo que está e segundo plano, esté activo o detenido.

*$BG (background)*

Sintaxis: bg [jobspec] <br>
Mueve el trabajo jobspec a segundo plano como si se hubiese iniciado con "&". Si el proceso especificado está detenido bg reinicia en segundo plano.

*$NOHUP*

Sintaxis: nohup orden [argumentos] <br>
La orden nohup lanza un proceso independiente del terminal que hemos usado. Básicamente lo que hace es ignorar la señal HUP (que se envía a un proceso cuando la terminal que lo controla se cierra).

### 5. Prioridad de procesos desde el terminal

Cada proceso tiene una determinada prioridad de ejecución, al necesitar más o menos CPU que otros. Normalmente la prioridad de los procesos es gestionada por el kernel automáticamente, no obstante Linux ofrece la posibilidad de modificar estas prioridades.

La prioridad de un proceso puede determinarse examinando la columna PRI en los resultados de los comandos top y ps -l. Los valores mostrados son relativos, cuanto es mayor el PRI mayor es el tiempo de CPU dedicado por el kernel a ese proceso.

El parámetro dice puede tomar valores comprendidos entre -20 y +19. Cualquier usuario puede aumentar el valor de nice y bajar la prioridad del proceso pero únicamente el usuario root puede asignar números negativos a nice y por lo tanto incrementar la 
prioridad y el tiempo de CPU.

*$NICE*

Sintaxis: nice [-n nicenumber | -nicenumer] command

El comando nice se usa para iniciar un proceso y proporcionarle un determinado valor. Para los usuarios normales está comprendido entre el 1 y 19. Para root los valores pueden tomar entre -20 y 19 Un número más bajo incrementa la prioridad de ejecución de un proceso.























