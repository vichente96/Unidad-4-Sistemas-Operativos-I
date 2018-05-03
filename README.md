# Unidad-4-Sistemas-Operativos-I

Asignación de fichero
Asignación de fichero indexado:
Asignación Indexada
También conocido como asignación por "I-Nodes" (nodos indexados), este método lleva el rastro de que bloque pertenece a cada archivo, asignando un I-node con todos los punteros hacia los demás bloques en el orden correspondiente, para cada archivo existe un I-node. El I-node lista los atributos y las direcciones de bloques del archivo asociado, por lo que dado su I-nodo, es posible encontrar todos los bloques de un Archivo. Existe perdida de espacio ya que cada archivo necesitar un I-nodo independiente de cuantos datos contenga el bloque. El rendimiento depende del archivo si se accede de manera secuencial o aleatoria, o si el archivo es muy grande o muy pequeño.

Asignación de ficheros contigua:
 Asignación Contigua
Como el nombre lo dice, los bloques que pertenecen a un mismo archivo se ubican de manera contigua. lo que es particularmente útil en el caso de los discos mecánicos ya que no es necesario realizar grandes movimientos en el cabezal para leer el archivo. También reduce las búsquedas en el disco, ya que se sabe que están en cierto espacio contiguo y no es necesario explorar todo para llegar a la información deseada. Cada directorio contiene, para cada archivo, la dirección del bloque en que comienza y la longitud del área asignada a este archivo.

Asignación de ficheros encadenada
Asignación Enlazada
Cada archivo es una lista ligada de bloques de disco, en cada bloque existe un puntero que direciona hacia el bloque siguiente, el resto del bloque es usado para almacenar datos, de esta forma, todos los bloques del disco pueden ser usados.

Base de datos:
Definición de base de datos
Base de Datos: es un conjunto de información relacionada que se encuentra agrupada o estructurada. Un archivo por sí mismo no constituye una base de datos, sino más bien la forma en que está organizada la información es la que da origen a la base de datos.

Bloque:
Concepto de Bloque.
En los dispositivos de almacenamiento secundario (discos duros, por ejemplo), la información se agrupa en bloques. Cada archivo está compuesto por 1 o varios bloques, y a su vez cada bloque está ubicado en un número de sectores.
La elección del tamaño del bloque es importante, ya que los bloques siempre se asignan completos, por lo que la parte sobrante no se puede utilizar.
Si el bloque es demasiado grande, se desperdicia espacio.
Si el bloque es muy pequeño, se aumenta el tiempo.
Tamaños típicos de bloque: 512 bytes, 1 Kb y 2 Kb
Campo
Campo clave:
Campos clave
En cualquier base de datos los registros incluidos en sus diferentes tablas deben estar perfectamente identificados y de esto se encargan las claves o llaves. Trasladando este concepto a la vida real, cada ciudadano tiene un número de DNI, puede haber dos personas con igual nombre e incluso apellidos iguales, pero ambos se diferenciarán por su número de DNI, que es único en "teoría"

Directorio
Directorio de trabajo o actual: 
Directorio de trabajo actual
En cualquier momento, se asume que los órdenes que introduce se refieren a su directorio de trabajo actual. Puede entender directorio de trabajo como el directorio en el que ''se encuentra'' en ese momento. Cuando accede por primera vez al sistema, su directorio de trabajo se configura como su directorio de usuario --/home/larry, en nuestro caso. Cuando haga referencia a un fichero, puede referirse a él en relación a su directorio de trabajo actual, en vez de especificar el nombre de la ruta completa del fichero

Fichero
Fichero de acceso directo o hash
Fichero indexado
Son los modos de disponer los registros del fichero en el soporte. Existen tres modos principales:
•	Directo: Los registros binarios no se disponen en el soporte atendiendo a un algoritmo de cálculo.
•	Indexado: Los registros generalmente se almacenan secuencialmente y van con un índice.

Fichero secuencial
Los registros se almacenan por posición, cada registro tiene el mismo tamaño y el mismo número de campos. El primero de cada registro de un campo se lee como campo clave, para leer un archivo el sistema comienza al principio del archivo y lee un registro a la vez hasta llegar al registro deseado. 
Es la forma más común de estructura de archivos.
Se emplea un formato fijo para los registros, son de la misma longitud y constan del mismo número de campos de tamaño fijo con un orden determinado.
Se necesita almacenar los valores de cada campo; el nombre del campo y la longitud de cada uno son atributos de la estructura del archivo. Cada registro tiene un campo clave que lo identifica (generalmente es el primero de cada registro). Los registros se almacenan en secuencia por la clave.
            Se utilizan normalmente en aplicaciones de procesos por lotes, ya que es la única organización de archivos que se puede guardar tanto en cintas como en discos.

Fichero secuencial indexado
Posee varias características que el archivo secuencial ya que se organizan en campos. Este método supera las desventajas del otro método. Este tiene un índice del archivo que permite llegar rápidamente a un registro deseado, esto se le llama archivo de desbordamiento, y se ejecuta a través de la dirección de punteros donde están ubicados en los registros deseados.

Los registros se organizan en una secuencia basada en un campo clave presentando dos características, un índice del archivo para soportar los accesos aleatorios y un archivo de desbordamiento. El índice proporciona una capacidad de búsqueda para llagar rápidamente al  registro deseado y el archivo de desbordamiento es similar al archivo de registros usado en un archivo secuencial, pero está integrado de forma que los archivos de desbordamiento se ubiquen siguiendo un puntero desde su registro predecesor.

La estructura más simple tiene como índice un archivo secuencial simple, cada registro del archivo índice tiene dos campos, un campo clave igual al del archivo principal y un puntero al archivo principal. Para encontrar un campo especifico se busca en el índice hasta encontrar el valor mayor de la clave que es iguale o precede al valor deseado de la clave, la búsqueda continua en el archivo principal a partir de la posición que indique el puntero.
Método de acceso
Es la estructura lógica de cada registro por la cual se acceden a ellos, esto significa que su almacenamiento secundario  depende de la agrupación y la asignación de cada uno de los archivos.  En la organización de estos archivos hay varias reglas importantes como: acceso rápido para recuperar la información de este, fácil de actualizar el archivo, economía de almacenamiento, mantenimiento simple, confianza para asegurar los datos.

Estas reglas se utilizan dependiendo de las tareas que va a usar el archivo; las estructuras utilizadas para estos manejos de archivos son diversas y puede implementarse como una combinación como: pilas, archivos secuenciales, archivos secuenciales indexados y archivos directos o de dispersión. La cual cada una de ellas definiremos más adelante.

Nodo-i
Un archivo posee varios componentes: un nombre, contenido e información administración como permiso y fechas de modificación. La información administrativa esta almacenada en el “ nodo-i ”( en ingles muchas veces se usa inodo ( sin guión) en vez de i-nodo), junto con datos esenciales para el sistema tales como su longitud, la región del disco en la que se encuentra almacenado el contenido del archivo y otros elementos.

Existen tres fechas en un i-nodo: la fecha en la que se hizo la ultima modificación ( escrita ) al contenido del archivo, la fecha en la que dicho contenido fue usado ( leído o ejecutado ) por ultima vez y la fecha en la que el i-nodo fue alterado por ultima vez, por ejemplo, para definir los permisos.


El nombre de archivo en un directorio se llama liga ( link) ya que une un nombre en la jerarquía de directorio al nodo-i y, en consecuencia, a los datos. El mismo numero-i puede aparecer en mas de un directorio.

Por lo tanto el nodo-i es un registro que almacena información sobre el archivo determinado y contiene:


 Identificación de usuario y de grupos de archivos.

 Instantes del ultimo acceso y de la ultima modificación.

 Contador con él numero de HORD-LINK al archivo.

 El tipo de archivo.

Pila
Una pila (stack en inglés) es una lista ordenada o estructura de datos que permite almacenar y recuperar datos, el modo de acceso a sus elementos es de tipo LIFO (del inglés Last In, First Out, «último en entrar, primero en salir») . Esta estructura se aplica en multitud de supuestos en el área de informática debido a su simplicidad y capacidad de dar respuesta a numerosos procesos.

Registro
un registro es una memoria de alta velocidad y poca capacidad, integrada en el microprocesador, que permite guardar transitoriamente y acceder a valores muy usados, generalmente en operaciones matemáticas.
•	Los registros de datos se usan para guardar números enteros. En algunas computadoras antiguas, existía un único registro donde se guardaba toda la información, llamado acumulador.
•	Los registros de memoria se usan para guardar exclusivamente direcciones de memoria. Eran muy usados en la arquitectura Harvard, ya que muchas veces las direcciones tenían un tamaño de palabra distinto que los datos.
•	Los registros de propósito general (en inglés GPRs o General Purpose Registers) pueden guardar tanto datos como direcciones. Son fundamentales en la arquitectura de von Neumann. La mayor parte de las computadoras modernas usa GPR.
•	Los registros de coma flotante se usan para guardar datos en formato de coma flotante.
•	Los registros constantes tienen valores creados por hardware de sólo lectura. Por ejemplo, en MIPS el registro cero siempre vale 0.
•	Los registros de propósito específico guardan información específica del estado del sistema, como el puntero de pila o el registro de estado.

Ruta del nombre
Casi todos los sistemas de archivos permiten organizar la información en carpetas. Este método de organización es muy segura. Permite que los programas funcionen mejor y la información está más ordenada.

Para indicar donde se encuentra un archivo, se usa una cadena de texto llamada “ruta”. Su aspecto cambia un poco de sistema a sistema: su estructura suele indicar las carpetas y subcarpetas que hay que recorrer para llegar al archivo, terminando con el nombre del mismo.

Las rutas no nos sirven solamente a nosotros como usuarios, sino también al sistema operativo para saber donde se encuentran ciertos archivos que uno u otro programa puede necesitar para funcionar.

Sistema de gestión de ficheros
Gestión de archivos: es la administración de los archivos esto se realiza a través del sistema operativo permitiendo  que los usuarios tengan acceso directo con los archivos y tengan control de ellos, así como también se puede enviar y compartir archivos con otros usuarios, brindarles seguridad y protección a estos. De modo que le permite al usuario realizar ciertas operaciones con ellos, las cuales son:
1)      Puedes crear un archivo, identificándolo con un nombre y determinar el espacio de este.
2)      Abrir el archivo, aquí se realiza distintas operaciones como su ejecución, leerlo, escribir en el.
3)      Borrarlo de modo que puedes liberar el espacio que ocupa este archivo.
4)      Cerrar el archivo, finaliza la ejecución de este.
5)      Modificarlo permite hacer cambios al archivo como cambiar su nombre.

Tabla de asignación de disco
 

Tabla de bits
 
