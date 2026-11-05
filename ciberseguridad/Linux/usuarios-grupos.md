# Usuarios, grupos y permisos en Linux

Para que Linux sea un sistema bastante seguro como lo es, se debe a que existen distintos tipos de usuarios dentro del sistema operativo los cuales cada uno cuenta con diferentes permisos específicos para que así otras personas o usuarios no accedan en áreas que no deberían.

<img width="438" height="286" alt="image" src="https://github.com/user-attachments/assets/14f0fa93-b2ab-42f5-a28c-e5e5982ed358" />

## Tipos de usuarios en Linux

### Admin o No-admin

Un usuario de Linux puede ser administrador o no-administrador. El administrador es como un supervisor (root) con todo el control sobre el sistema. Es importante asegurarse que solo una pequeña cantidad de personas tienen permisos de lectura y escritura en todos los archivos del sistema. Por el contrario el no-administrador por defecto tiene acceso limitado a ciertas configuraciones de archivos dentro del sistema.

### Usuario normal

La mayoría de las cuentas serán no-administrador. Estos usuario pueden ser divididos en dos subtipos: usuarios normales o usuarios del sistema, los usuarios normales son personas reales. Se les dan individualmente una cuenta para loggearse y tener acceso limitado para las aplicaciones del computador, archivos y recuros.

### Usuario del sistema

Es una cuenta generada dentro del computador, no es una persona real. Son creados para correr programas o procesos específicos como puede ser el respaldo de un programa. Este tipo de "usuario" tiene control limitado y solo se le asigna el acceso necesario para manejar ese proceso en particular.

## Usuarios y grupos en Linux

En un sistema de Linux, todos los usuarios que son agregados se les asignan un nombre, una identificación única de usuario (UID), grupo, y número de identificación de grupo (GID). Cuando el usuario se crea inicialmente, un nuevo UID y GID son asignados.

- Administrador (root): UID y GID = 0
- Usuario del sistema (generado por computador): UID y GID asignado desde 1 hasta 999
- Usuarios normales (personas reales): UID y GID = 1000 o mayor, se incrementa con cada usuario nuevo.













