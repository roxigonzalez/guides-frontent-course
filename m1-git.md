# GIT

## Conceptos Básicos

**¿Qué es control de versiones?**
El control de versiones es un sistema que registra los cambios realizados sobre un archivo o conjunto de archivos a lo largo del tiempo, de modo que puedas recuperar versiones específicas más adelante.

**¿Qué es GIT?**
es un software de control de versiones diseñado por Linus Torvalds, pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente. Su propósito es llevar registro de los cambios en archivos de computadora y coordinar el trabajo que varias personas realizan sobre archivos compartidos.

**Git añade información**
Cuando realizas acciones en Git, casi todas ellas sólo añaden información a la base de datos de Git. Es muy difícil conseguir que el sistema haga algo que no se pueda deshacer, o que de algún modo borre información.

**Estados de GIT**

Git tiene tres estados principales en los que se pueden encontrar tus archivos: **confirmado** (committed), **modificado** (modified), y **preparado** (staged).

- **Confirmado** significa que los datos están almacenados de manera segura en tu base de datos local.

- **Modificado** significa que has modificado el archivo pero todavía no lo has confirmado a tu base de datos.

- **Preparado** significa que has marcado un archivo modificado en su versión actual para que vaya en tu próxima confirmación.

El flujo de trabajo básico en Git es algo así:

1. **Modificas** una serie de archivos en tu directorio de trabajo.
2. **Preparas** los archivos, añadiendolos a tu área de preparación.
3. **Confirmas** los cambios, lo que toma los archivos tal y como están en el área de preparación, y almacena esas instantáneas de manera permanente en tu directorio de Git.

Si una versión concreta de un archivo está en el directorio de Git, se considera **confirmada** (committed). Si ha sufrido cambios desde que se obtuvo del repositorio, pero ha sido añadida al área de preparación, está **preparada** (staged). Y si ha sufrido cambios desde que se obtuvo del repositorio, pero no se ha preparado, está **modificada** (modified).

## Instalación y configuración de GitHub

**Instalación**
https://git-scm.com/download/win

**Despúes de instalar Git**

Establecer tu nombre de usuario y dirección de correo electrónico. Esto es importante porque las confirmaciones de cambios (commits) en Git usan esta información, y es introducida de manera inmutable en los commits que envías:

```
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

Para ver tus configuraciones puedes correr esta línea de comando:
git config --list

## Inicializando un repositorio en un proyecto existente.

Ir al directorio del proyecto y escribir:

```
git init
```

Esto crea un nuevo subdirectorio llamado .git que contiene todos los archivos necesarios del repositorio —un esqueleto de un repositorio Git.

## Clonando un repositorio

Si deseas obtener una copia de un repositorio Git existente —por ejemplo, un proyecto en el que te gustaría contribuir— el comando que necesitas es `git clone`.

Puedes clonar un repositorio con git clone [url]. Por ejemplo, si quieres clonar la librería Ruby llamada Grit, harías algo así:

```bash
$ git clone git://github.com/schacon/grit.git
```

Esto te creará una carpeta grit con los archivos del repositorio. Pero si deseas descargar los archivos de ese repositorio grit en un nombre de carpeta diferente debes hacer lo siguiente:

```
$ git clone git://github.com/schacon/grit.git mygrit
```

## Estado de los archivos

```bash
$ git status
# On branch master
nothing to commit, working directory clean
```

Esto significa que tienes un directorio de trabajo limpio —en otras palabras, no tienes archivos bajo seguimiento y modificados—. Git tampoco ve ningún archivo que no esté bajo seguimiento, o estaría listado ahí. Por último, el comando te dice en qué rama estás.

### Órdenes básicas

`git fetch`

Descarga los cambios realizados en el repositorio remoto.

`git pull`

Unifica los comandos fetch y merge en un único comando.

`git commit -am "<mensaje>"`

Confirma los cambios realizados. El “mensaje” generalmente se usa para asociar al commit una breve descripción de los cambios realizados.

`git push origin <nombre_rama>`

Sube la rama “nombre_rama” al servidor remoto.

`git status`

Muestra el estado actual de la rama, como los cambios que hay sin commitear.

`git add <nombre_archivo>`

Comienza a trackear el archivo “nombre_archivo”.

`git checkout -b <nombre_rama_nueva>`

Crea una rama a partir de la que te encuentres parado con el nombre “nombre_rama_nueva”, y luego salta sobre la rama nueva, por lo que quedas parado en esta última.

`git checkout -t origin/<nombre_rama>`

Si existe una rama remota de nombre “nombre_rama”, al ejecutar este comando se crea una rama local con el nombre “nombre_rama” para hacer un seguimiento de la rama remota con el mismo nombre.

`git branch`

Lista todas las ramas locales.

`git branch -a`

Lista todas las ramas locales y remotas.

`git branch -d <nombre_rama>`

Elimina la rama local con el nombre “nombre_rama”.

`git push origin <nombre_rama>`

Commitea los cambios desde el branch local origin al branch “nombre_rama”.

`git reset --hard HEAD`

Elimina los cambios realizados que aún no se hayan hecho commit.

`git merge <nombre_rama>`

Impacta en la rama en la que te encuentras parado, los cambios realizados en la rama “nombre_rama”.

## Flujo de Trabajo (IDEAL)

Muchos desarrolladores que usan Git llevan un flujo de trabajo de esta naturaleza, manteniendo en la rama master únicamente el código totalmente estable o en producción (el código que ha sido o que va a ser liberado).

Se deben utilizar 4 tipos de ramas: _Master_, _Development_, _Features_, y _Hotfix_.

**Master**

Es la rama principal. Contiene el repositorio que se encuentra publicado en producción, por lo que debe estar siempre estable.

**Development**

Es una rama sacada de master. Es la rama de integración, todas las nuevas funcionalidades se deben integrar en esta rama. Luego que se realice la integración y se corrijan los errores (en caso de haber alguno), es decir que la rama se encuentre estable, se puede hacer un merge de development sobre la rama master.

**Features**

Cada nueva funcionalidad se debe realizar en una rama nueva, específica para esa funcionalidad. Estas se deben sacar de development. Una vez que la funcionalidad esté desarrollada, se hace un merge de la rama sobre development, donde se integrará con las demás funcionalidades.

**Hotfix**

Son bugs que surgen en producción, por lo que se deben arreglar y publicar de forma urgente. Es por ello, que son ramas sacadas de master. Una vez corregido el error, se debe hacer un merge de la rama sobre master. Al final, para que no quede desactualizada, se debe realizar el merge de master sobre development.
