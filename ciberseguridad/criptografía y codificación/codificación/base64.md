# Base64

Base 64 es un sistema de numeración posicional que usa 64 como base. Esta se usa bastante como puede ser para la codificación de correos electrónicos, PGP y otras aplicaciones. Todas las variantes famosas que se conocen con el nombre de Base64 usan el rango de caracteres A-Z, a-z, 0-9 en ese orden para los primeros 62 dígitos, pero los símbolos escogidos para los últimos dos dígitos varían considerablemente de unas a otras.

## Esquemas de codificación en Base64

Existen varios esquemas que están relacionados con Base64, pero tienen diferencias en su propósito, alfabeto, formato de salida, relleno y validación de los datos. Algunos utilizan Base64 estándar con pequeñas modificaciones, mientras que otros añaden mecanismos adicionales o adaptan la codificación a un protocolo específico.

### Comparación general

| **Esquema** | **Propósito principal** | **Diferencia respecto a Base64 estándar** |
|----------|----------|----------|
| PEM   | Transmitir mensajes de correo electrónico de forma segura.   | Utiliza Base64 para representar datos binarios mediante caracteres imprimibles y establece reglas de formato, como líneas de 64 caracteres.|
| MIME    | Permitir el envío de contenido multimedia y archivos mediante correo electrónico   | Utiliza el alfabeto Base64 estándar, pero permite líneas de hasta 76 caracteres.|
| UTF-7    | Representar texto Unicode utilizando caracteres ASCII | Utiliza una variante llamada Modified Base64, que omite el carácter de relleno =. |
| OpenPGP    | Representar datos protegidos mediante criptografía en un formato textual. | Utiliza Base64 y añade una suma de verificación CRC de 24 bits.|
| IRCu (P10)    | Representar identificadores y datos numéricos dentro de un protocolo IRC.  | Utiliza un alfabeto modificado y adaptado al protocolo; no necesita relleno en sus campos de longitud fija. |
| RFC 3548    | Unificar las especificaciones de Base16, Base32 y Base64.  | Estableció reglas comunes para estas codificaciones. Fue reemplazado por el RFC 4648. |
| RFC 4648    |	Estandarizar Base16, Base32 y Base64. | Define las reglas generales de estas codificaciones y aspectos como el relleno, los saltos de línea y los alfabetos alternativos. |

## Ejemplo

Una cita de Thomas Hobbes perteneciente a la obra Leviarhan:

*Man is distinguished, not only by his reason, but by this singular passion from other animals, which is a lust of the mind, that by a perseverance of delight in the continued and indefatigable generation of knowledge, exceeds the short vehemence of any carnal pleasure.*

Se codifica en Base64 como:

*TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdCBvbmx5IGJ5IGhpcyByZWFzb24sIGJ1dCBieSB0aGlz
IHNpbmd1bGFyIHBhc3Npb24gZnJvbSBvdGhlciBhbmltYWxzLCB3aGljaCBpcyBhIGx1c3Qgb2Yg
dGhlIG1pbmQsIHRoYXQgYnkgYSBwZXJzZXZlcmFuY2Ugb2YgZGVsaWdodCBpbiB0aGUgY29udGlu
dWVkIGFuZCBpbmRlZmF0aWdhYmxlIGdlbmVyYXRpb24gb2Yga25vd2xlZGdlLCBleGNlZWRzIHRo
ZSBzaG9ydCB2ZWhlbWVuY2Ugb2YgYW55IGNhcm5hbCBwbGVhc3VyZS4=*


En la cita de arriba el valor codificado de *Man* es TWFu. Codificadas en ASCII, las letras: M, a y n son almacenadas como los bytes 77, 97 y 110, es decir, 01001101, 01100001, 01101110 en base 2.

Ahora esos tres bytes se unen y tenemos el búfer de 24 bits, que será 010011010110000101101110. Este número se convertirá a su valor Base64, que puede hacerse tomando bloques de 6 bits a la vez (6 bits forman como máximo 64 valores diferentes en binario: 26). A continuación, cogiendo cada vez 6 bits del búfer, tenemos 4 números (24 = 6 x 4), que entonces son convertidos a su correspondiente valor en Base64.

<img width="362" height="86" alt="image" src="https://github.com/user-attachments/assets/3bf9f55a-3636-4011-af76-f7f82ac0500c" />
















