# *¿Qué es GIT?*  

Es un **sistema** de control de versiones distribuido gratuito y de código abierto diseñado para manejar proyectos grandes y pequeños con rapidez y eficiencia. 

Fue desarrollado por Linus Torvalds en 2005. Su fin es tener el registro de los cambios de los archivos, así como coordinar el trabajo que varias personas realizan sobre archivos compartidos en un repositorio de código.
Ocupa poco espacio con un rápido rendimiento, cuenta con características como sucursales locales económicas, áreas de preparación convenientes y múltiples flujos de trabajo.

Al contar con arquitectura distribuida, es un ejemplo de DVCS (sistema de control de versiones distribuido, por sus siglas en inglés). En lugar de tener un único espacio para todo el historial de versiones del software, como sucede con los sistemas de control populares como CVS o Subversion (también conocido como SVN), en Git, la copia de trabajo del código de cada desarrollador es también un repositorio que puede albergar el historial completo de todos los cambios. Git se ha diseñado teniendo en cuenta el rendimiento, la seguridad y la flexibilidad.

# *Ramificación y Fusión*

La característica de Git que lo diferencia de otros SCM es su modelo de ramificación que permite y alienta a tener varias sucursales locales que pueden ser completamente independientes entre sí. La creación, fusión y eliminación de esas líneas de desarrollo toma solo unos segundos. Esto permite:

* Realizar cambios de contexto: se puede crear una rama para probar una idea, realizar un commit varias veces y regresar en donde se ramificó, aplicar un parche, regresar en donde se está experimentando y hacer una combinación.
*	Líneas de código basadas en roles: se puede tener una rama que contenga solo lo que va a producción, otra en la que se hagan pruebas y otras para el trabajo diario.
*	Flujo de trabajo basado en características: se pueden crear nuevas ramas para cada función nueva en la que se esté trabajando para alternar entre ellas sin problema. Luego se puede eliminar cada rama cuando esa función se fusione con su línea principal.
*	Experimentación desechable: se puede crear una rama para experimentar y si no va a funcionar simplemente se borra sin que nadie más la vea (incluso si se han enviado otras ramas mientras tanto).

Cuando se hace un envío a un repositorio remoto no es necesario enviar todas sus ramificaciones, se puede elegir compartir solo una, algunas o todas ellas. Esto tiende a liberar a las personas para probar nuevas ideas sin preocuparse por tener que planificar cómo y cuándo van a fusionarlas o compartirlas con otros.
Esto también se puede realizar con otros sistemas pero conlleva más trabajo y es más difícil. Git hace que este proceso sea más fácil y cambia la forma en que la mayoría de los desarrolladores trabajan cuando lo aprenden.

# *Rendimiento*

Git realiza casi todas las operaciones localmente, lo que le brinda una gran velocidad en sistemas centralizados que constantemente tienen que comunicarse con un servidor.

Git fue creado para funcionar en el kernel de Linux, lo que significa que ha tenido que manejar de manera efectiva grandes repositorios. Git fue desarrollado en C, lo que reduce la sobrecarga de los tiempos de ejecución asociados con los lenguajes de nivel superior. La velocidad y el rendimiento han sido un objetivo de diseño principal de Git desde el principio.

Comparando operaciones comunes de GIT y SVN en pruebas con instancias de AWS en la misma zona de disponibilidad, GIT puede ser de 3 o 16 veces más rápido que GIT aún en las mejores condiciones de operación para SVN la diferencia se haría todavía más grande si la conexión fuera más lenta lo cual no afectaría a GIT. Esto significa que GIT es más rápido que SVN en condiciones ideales.
Un aspecto donde Git es más lento es en la operación de clonación inicial porque GIT descarga todo el historial en lugar de solo la última versión. A pesar de esto, el tamaño de todo el historial y todas las versiones, no difiere mucho de los datos en el lado del cliente, lo que ilustra lo eficiente que es comprimir y almacenar datos en el lado del cliente.

# *Sistema Distribuido*

Esto significa que en lugar de hacer una "verificación" del código fuente actual, hace un "clon" de todo el repositorio.
Git le da a cada programador una copia local del historial del desarrollo entero, y los cambios se propagan entre los repositorios locales. Los cambios se importan como ramas adicionales y pueden ser fusionados en la misma manera que se hace con la rama local.
Múltiples copias de seguridad
Incluso si está utilizando un flujo de trabajo centralizado, cada usuario tiene esencialmente una copia de seguridad completa del servidor principal. Cada una de estas copias se podría empujar hacia arriba para reemplazar el servidor principal en caso de falla o corrupción. Todo esto podría fallar a menos que solo haya una única copia del repositorio.

# *¿Dónde almacena Git la información?*
Cada uno de los proyectos de Git tiene dos partes: los archivos y directorios que se crea y edita directamente y la información adicional que registra Git sobre el historial del proyecto. La combinación de estas dos cosas se llama repositorio.
Git almacena toda su información adicional en un directorio llamado .git ubicado en el directorio raíz del repositorio. Git espera que esta información se presente de manera muy precisa, por lo que nunca se debe editar ni eliminar nada en .git.

# *Flujos de trabajo*

Git plantea una gran libertad en la forma de trabajar en torno a un proyecto pero para coordinar el trabajo de un grupo de personas en torno a un proyecto se utiliza un flujo de trabajo que es una fórmula o una recomendación acerca del uso de Git para realizar trabajo de forma uniforme y productiva. Los flujos de trabajo más populares son git-flow, GitHub-flow, GitLab Flow y One Flow

Debido a la naturaleza distribuida de Git y al sistema de bifurcación, se puede implementar una gran cantidad de flujos de trabajo. Es flexible en la capacidad para gestionar varios tipos de flujos de trabajo de desarrollo no lineal, en su eficiencia en proyectos tanto grandes como pequeños y en su compatibilidad con numerosos sistemas y protocolos.
Git se ha ideado para posibilitar la ramificación y el etiquetado como procesos de primera importancia (a diferencia de SVN) y las operaciones que afectan a las ramas y las etiquetas (como la fusión o la reversión) también se almacenan en el historial de cambios. No todos los sistemas de control de versiones ofrecen este nivel de seguimiento.

## *Flujos*

*	**Git-Flow**: es el flujo más conocido y está pensado para proyectos con entregables y ciclos de desarrollo bien definidos. Está basado en dos grandes ramas con tiempo de vida infinito (master y develop) y varias ramas de apoyo, unas orientadas al desarrollo de nuevas funcionalidades (ramas feature-*), otras al arreglo de errores (hotfix-*) y otras orientadas a la preparación de nuevas versiones de producción (ramas release-*).

*	**GitHub-Flow**: creado en 2011 por GitHub. Está centrado en un modelo de desarrollo iterativo y de despliegue constante. Intenta simplificar la gestión de ramas, trabajando directamente sobre la rama master e integrando las distintas funciones a esta rama
 
    Está basado en cuatro principios: 

    1.	Todo lo que está en la rama master está listo para ser puesto en producción
    2.	Para trabajar en algo nuevo, se crea una nueva rama desde la master.
    3.	Cuando creemos que la rama está lista para integrarla en la rama master, se debe abrir una pull request (solicitud de integración de cambios).
    4.	Alguien debe revisar y visar los cambios para fusionarlos con la rama master


*	**Flujo de administrador de integración**: otro flujo de trabajo común de Git implica un administrador de integración (una sola persona que realiza commits hacia el repositorio 'bendecido'). Luego, varios desarrolladores clonan desde ese repositorio, lo envían a sus propios repositorios independientes y le piden al integrador que incorpore sus cambios. Este es el tipo de modelo de desarrollo que se ve a menudo con repositorios de código abierto o GitHub.

*	**Flujo de dictadores y tenientes**: este flujo suele ser más efectivo para proyectos masivos. En este modelo, algunas personas ('lugartenientes') están a cargo de un subsistema específico del proyecto y fusionan todos los cambios relacionados con ese subsistema. Otro integrador (el 'dictador') puede extraer cambios solo de sus lugartenientes y luego enviarlos al repositorio 'bendito' del que todos clonan nuevamente.

# *Seguridad*
El modelo de datos que utiliza Git garantiza la integridad criptográfica de cada parte del proyecto. Cada archivo y commit se verifica y se recupera mediante su verificación cuando regresa. Es imposible obtener algo de Git que no sea exactamente lo que se ingresó.

También es imposible cambiar cualquier archivo, fecha, mensaje de confirmación o cualquier otro dato en un repositorio de Git sin cambiar las ID de todo lo que sigue. Esto significa que si tiene una ID de commit, puede estar seguro no solo de que su proyecto es exactamente igual que cuando se hizo el commit, sino que no se cambió nada en su historial.

La mayoría de los sistemas de control de versiones centralizados no proporcionan tal integridad por defecto.
Git se ha diseñado con la principal prioridad de conservar la integridad del código fuente gestionado. El contenido de los archivos y las relaciones entre estos y los directorios, las versiones, las etiquetas y las confirmaciones, todos objetos del repositorio de Git, están protegidos con un algoritmo de hash criptográficamente seguro llamado "SHA1". De este modo, se salvaguarda el código y el historial de cambios frente a las modificaciones accidentales y maliciosas, y se garantiza que el historial sea totalmente trazable.

# *Área de Preparación*

Git tiene algo llamado "área de preparación" o "índice". Esta es un área intermedia donde se pueden formatear y revisar los commits antes de completar el mismo.
En Git es posible almacenar rápidamente archivos y enviarlos sin enviar todos los demás archivos modificados en el directorio de trabajo o tener que enumerarlos en la línea de comandos durante la confirmación. Esto permite organizar solo partes de un archivo modificado.  

Ahora puede preparar el cambio que necesita para el commit actual y preparar el otro cambio para el siguiente commit. Esta función se amplía a tantos cambios diferentes en su archivo como sea necesario. Por supuesto, Git también hace que sea fácil ignorar esta función si no desea ese tipo de control: simplemente agregue una '-a' a su comando de confirmación para agregar todos los cambios a todos los archivos en el área de preparación.

# *Gratis y de código abierto*

Git se publica bajo la Licencia Pública General GNU versión 2.0, que es una licencia de código abierto. El proyecto Git eligió usar GPLv2 para garantizar su libertad para compartir y cambiar el software libre, para asegurarse de que el software sea gratuito para todos sus usuarios.

# *Cómandos Principales*

* *git init*: crea un subdirectorio nuevo llamado .git, que contiene todos los archivos necesarios del repositorio – un esqueleto de un repositorio de Git. Todavía no hay nada en tu proyecto que esté bajo seguimiento.

* *git status*: muestra el estado actual de la rama, como los cambios que hay sin commitear. También muestra: 
  * Si hay algo para confirmar, enviar o recibir (pull).
  * Si hay archivos en preparación (staged), sin preparación(unstaged) o que no están recibiendo seguimiento (untracked)
  * Si hay archivos creados, modificados o eliminados

* *git add <nombre_archivo>*: comienza a registrar el historial del archivo “nombre_archivo”.

  * *git add -a*: añade todo

* *git fetch*: descarga los cambios realizados en el repositorio remoto.

* *git clone*: Git clone es un comando para descargar el código fuente existente desde un repositorio remoto (como Github, por ejemplo). En otras palabras, básicamente realiza una copia idéntica de la última versión de un proyecto en un repositorio y la guarda en tu ordenador.

* *git merge <nombre_rama>*: cuando se haya completado el desarrollo del proyecto en la rama actual y todo funcione correctamente, el último paso es fusionar la rama con su rama padre (dev o master). Integra las características de la rama con todos los commits realizados a las ramas dev (o master).  Es importante recordar que hay que estar posicionado en esa rama específica para fusionarla  con la rama principal.

* *git pull*: se utiliza para recibir actualizaciones del repositorio remoto, unificando los comandos fetch y merge en un único comando, lo cual significa que recogeremos actualizaciones del repositorio remoto (git fetch) e inmediatamente aplicamos estos últimos cambios en local (git merge).

* *git commit -m "<mensaje>"*: es como establecer un punto de control en el proceso de desarrollo al cual se puede volver más tarde si es necesario. Confirma los cambios realizados. El “mensaje” generalmente se usa para describir los cambios hechos al commit.
  
* *git push origin <nombre_rama>*: después de haber confirmado tus cambios, el siguiente paso es enviar los cambios al servidor remoto. Git push envía los commits al repositorio remoto. Sube la rama “nombre_rama” al servidor remoto.
 
   * *git push origin <nombre_rama>:* hace un commit de los cambios desde el branch local origin al branch “nombre_rama”.
  
* *git branch*: varios desarrolladores pueden trabajar en paralelo en el mismo proyecto simultáneamente. Podemos usar el comando git branch para crearlas, listarlas y eliminarlas.

  * *git branch -a*: lista todas las ramas locales y remotas.

  * *git branch -d <nombre_rama>*: elimina la rama local con el nombre “nombre_rama”.

* *git checkout*: para trabajar en una rama, primero hay que cambiarse a ella. Esta instrucción se usa para cambiar de una rama a otra. También se usa para chequear archivos y commits. Para ejecutar esto, los cambios en la rama actual tienen que ser confirmados o almacenados en el guardado rápido (stash) antes de que cambiar de rama.  La rama a la que se desea cambiar debe existir en local.
  
  * *git checkout -b <nombre_rama_nueva>*: crea una rama a partir de la actual con el nombre “nombre_rama_nueva”, y luego se posiciona en la rama nueva.

  * *git checkout -t origin/<nombre_rama>*: Si existe una rama remota de nombre “nombre_rama”, al ejecutar este comando se crea una rama local con el nombre “nombre_rama” para hacer un seguimiento de la rama remota con el mismo nombre.

* *git remote prune origin*: actualiza el repositorio remoto en caso que algún otro desarrollador haya eliminado alguna rama remota.

* *git reset --hard HEAD*: elimina los cambios realizados que aún no se hayan hecho commit.

* *git revert <hash_commit>*: revierte el commit realizado, identificado por el “hash_commit”. El comando deshará el commit indicado, pero creará un nuevo commit deshaciendo la anterior. No afecta al commit histórico. Por lo que se puede seguir viendo todos los commits en el histórico, incluso los revertidos. Otra medida de seguridad es que todo sucede en local a no ser que los enviemos al repositorio remoto. Por esto es que git revert es más seguro de usar y es la manera preferida para deshacer los commits.

