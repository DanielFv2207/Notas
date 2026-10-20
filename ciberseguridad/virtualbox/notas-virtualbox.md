# VIRTUALBOX

DEF - VirtualBox es un programa que permite crear máquinas virtuales dentro de un PC, en pocas palabras el sistema te permite instalar otros sistemas operativos ya sean Linux, Windows o macOS dentro de tu mismo sistema operativo, todo desde un mismo equipo.

## Historia:

VirtualBox fue creado por la empresa Innotek en el año 2007, y poco después fue adquirido por Sun Microsystems. En 2010, Oracle compró Sun microsystems y desde entonces el programa se conoce oficialmente como Oracle VM VirtualBox. 
Esta es una herramienta totalmente gratuita y de código abierto lo que la hace muy popular entre estudiantes, técnicos y desarrolladores.

## Máquinas virtuales

Dentro de las computadoras la virtualización se refiere a crear una versión simulada de algo ya sea un sistema operativo, servidor o redes. En lugar de ejecutar estos recursos en hardware físico, la virtualización permite crear entornos virtuales independientes que 
funcionan como si estuvisen en su propia maquina física, con la virtualización puedes explorar diferentes sistemas operativos como Windows, Linux y mac en la misma PC.

#### ¿Cómo funcionan las máquinas virtuales?
<img width="691" height="459" alt="image" src="https://github.com/user-attachments/assets/09178425-4710-4317-a29c-8929bdf09528" />
<br>
Para saber como funcionan voy a dividir por 4 capas: 
<br><br>

**HARDWARE:** Es la capa más fundamental ya que son todos los componentes que constituyen la infraestructura física sobre la cual se construyen estas maquinas virtuales, sin el hardware real no podríamos crear una maquina virtual ya que esta utiliza los recursos como
la memoria y el procesamiento.

**SISTEMA OPERATIVO:** Esta capa es la que pone una interfaz entre el hardware real y las aplicaciones que van a estar encima del sistema operativo, este sistema operativo se conoce como sistema operativo anfitrión o host, a este nos referimos al que se ejecuta
directamente desde el hardware físico de la PC, puede ser cualquier sistema operativo común.

**HYPERVISOR:** También visto como el software de virtualización, es una tecnología que actúa como una capa intermedia entre el sistema operativo y hardware de una computadora y las maquinas virtuales que van a vivir en la computadora, el hypervisor se encarga de 
gestionar eficientemente los recursos físicos del hardware como el CPU o la memoria, este se comunica con el sistema operativo por ejemplo en caso de que necesites una conexión red u otras cosas. Este también se encarga de aislar a cada máquina virtual para que cada
una sea independiente, también podemos tomar imágenes de cada máquina virtual, lo que significa que podemos transferir cada máquina a otra computadora.

**MÁQUINAS VIRTUALES:** Aquí tenemos hardware virtual, que realmente es una parte del hardware real que se usa para correr las máquinas virtuales, también está el sistema operativo de la máquina virtual que se ejecuta con el hardware virtual y encima ya tenemos
las aplicaciones que se ejecutan en el entorno virtual y estas se ejecutan como si estuvieran en su propia computadora física independiente.

           
