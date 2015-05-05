Branch donde vamos a subir todo lo relacionado al codigo del lado servidor

#### En este archivo les voy a poner algunas instrucciones para ir trabajando con git

Fecha: 03/05/2015 11:00 PM
Nota 1: El archivo solo se ve correctamente en GitHUB, asi que no se preocupen que si lo descargan se vea un solo deschonge :laughing:

Nota 2: Estos pasos son para Linux, pero supongo que pueden servir de idea de que se debe hacer en Windows

Nota 3: El archivo irá agregando mas tips segun necesitemos

Fecha 04/05/2015 5:00 PM

Nota 1: He cometido un error en las instrucciones para lo de el vinculado, en realidad no afecta en mucho pero es mejor estar prevenidos por cualquier cosa. Asi que borren la carpeta del proyecto y vuelvalon a clonar y hacer todos estos pasos otra vez :disappointed: 

## Instrucciones para el clonado y correcta sincronización de nuestro repositorio local con el repositorio en GitHUB:

1. Primero es importante clonar este repositorio, para esto es necesario colocarte dentro de una carpeta de su elección y ejecutar el siguiente comando en consola:
	```console
	git clone https://github.com/devkev95/Proyecto-HDP
	```
	Creo que el comando se explica solo 

2. Git automaticamente creará una carpeta donde se encontrarán los archivos de la rama principal de nuestro repositorio, BackEnd.

3. En linux hay un problema cuando se descargan repositorios(Al parecer en windows también existe este problema); git no crea localmente las demas ramas excepto la principal, en nuestro caso BackEnd, asi que hay que crearlas. Para esto ejecutamos el siguiene comando en consola:
	```console
	git checkout -t -b Reglas origin/Reglas
	```
	Un poco de explicación del comando anterior:
	El comando  checkout sirve para moverte de una rama a otra; si ejecutan este comando, bueno al menos en linux si sucede, verán que los archivos en la carpeta local del repositorio cambiarán de los de la rama anterior a la nueva rama a la cual se han movido. El modificador -b del comando checkout crea la rama que le digamos, en este caso Regla, antes de moverse a ella; osea que en este comando estamos creando y moviendonos a la rama que acabamos de crear al mismo tiempo. Por separado se puede realizar de la siguiente forma: 
	```console  
	git branch -t Reglas origin/Reglas 
	``` 
	y luego

	```console  
	git checkout Reglas 
	``` 
	El modificador -t nos permite hacer un seguimiento minucioso a los cambios que realizamos entre nuestro repositorio local y repositorio remoto, por ejemplo cada vez que hagamos checkout a una rama nos mostrará las diferencias de commits(luego explicaré que es eso) entre nuestro repositorio local y el remoto. La última parte del comado es una especie de vinculo, vincula nuestra rama actual con la rama del repositorio; por lo tanto cualquier cambio que realizamos en la rama local se vera reflejado en nuestro rama en el repositorio(Explicaré como se hace esto luego). Por lo tanto, para crear y vincular nuestras ramas locales tenemos que realizar este proceso para las ramas Reglas(si no la han creado y vinculado ya), Documento_Escrito y GUI. Por ejemplo: cambiando Reglas por Documento_Escrito y origin/Reglas por origin/Documento_Escrito.

## add, commit, push y pull

Bueno vamos a lo mero rico del asunto(uyyyy, que culer.... :laughing:). En general cuando realizamos un cambio en nuestro repositorio local queremos que estos cambios se vean reflejados en nuestro repositorio remoto. Veamos un pequeño ejemplo(en este caso el repositorio con el que trabajo es uno llamado test, no lo clonen es solo para ejemplificar).

Despues de haber clonado en el repositorio test en nuestra computadora, imaginemos que creamos dos archivos llamados hello_world.py y hello_world2.py en nuestro repositorio local. Para saber si estos archivos se le estan dando seguimiento en nuestro repositorio local, utilizamos el siguiente comando:
```console  
git status -s -u
```
El comando nos muestra los archivos a los cuales no se les esta dando seguimiento en el repositorio local, esto se hace con el modificador -u, y nos muestra la versión resumida de la informacion de estos archivos(el nombre de los archivos sin seguir), esto se hace con el modificador -s, si deseamos darle seguimiento, por ejemplo, al archivo hello_world.py utilizamos el siguiente comado:
```console  
git add hello_world.py
```
Si hubieramos deseado darle seguimiento a todos los archivos se utiliza la siguiente instruccion:
```console  
git add -A
```
El modificador -A le ordena al repositorio local darle seguimiento a todos los archivos que no son seguidos o actualizar los archivos que ya son seguidos.

Este seguimiento de los archivos es el que nos permite tomar una "captura" de el estado actual de nuestro proyecto para luego subir esta "captura" a nuestro repositorio remoto. Para tomar una "captura" del estado actual de nuestro repositorio local utilizamos el siguiente comando:
```console  
git commit -m "Esta es una actualización"
``` 
El comando anterior, como se dijo anteriormente, toma una "captura" de los archivos que actualmente se les esta dando seguimiento; el modificador -m sirve para poner un mensaje sobre el commit, en este caso "Esta es una actualización", si omitieramos este modificador git automaticamente nos pedira que agregemos un mensaje al commit.

Luego de realizar el commit, y para que nuestros cambios se vean reflejados en GitHUB, es necesario relizar el siguiente comando:
```console  
git push
``` 
El comando anterior es el que en realidad nos permite subir los cambios de nuestro repositorio local al repositorio remoto, despúes de haber ejecutado este comando git nos preguntará por nuestro nombre de usuario y contraseña de GitHUB despues de haber validadod las credenciales nos enviará un mensaje de exito y podremos ver en nuestro repositorio remoto los cambios.

Ya que generalmente, como en nuestro caso, no es una sola persona la que trabaje en el proyecto sino que un equipo de desarrollo, a veces un miembro del equipo realiza cambios en el repositorio remoto mientras estamos trabajando en nuestro repositorio local y cuando deseamos subir estos cambios que hemos realizado a nuestro repositorio remoto con la serie de comandos que realizamos anteriormente, git nos produce un error; esto es debido a que nuestro arbol de archivos locales no tiene la misma estructura que el arbol de archivos del repositorio o algunos archivos tiene diferencias con algunos archivos en el repositorio remoto. Pero git amigo nos muestra un consejo al mismo tiempo que el mensaje de error, en este caso nos pide que ejecutemos el comando 
```console  
git pull
``` 
para combinar el arbol de archivos de nuestro repositorio local con el de el repositorio remoto. Apunto que ejecutar el comando anterior no es una buena practica, es mejor usar primero el comando git fetch y luego git merge. En un link que pongo mas adelante en el archivo hay una explicación del porqué y opciones de como arreglar estas inconsistencias.

En nuestro caso una mejor opcion del comando anterior sería:
```console  
git pull --no-edit
```   
El comando anterior nos permite evitar que git nos pida un mensaje para justificar porque hemos realizado la combinación de nuestro arbol local de archivos con el del repositorio remoto, aunque en general recomiendo justificar porque hemos realizado cada cosa para mantener una mayor documentacion de lo que hemos hecho.

Por ultimo, solo como aclaración, todo este proceso solo tiene efecto en una rama especifica, por ejemplo si cambiamos un archivo de una rama y deseamos que los cambios de este archivo se vean reflejados en esa rama realizamos el proceso anterior y los cambios se verán reflejados en la rama del repositrio remoto, es decir, que este proceso lo tenemos que realizar por cada cambio que realizemos en cada rama de nuestro repositorio local para que se vean reflejados en nuestro repositorio remoto. 

P.D : Si hay algun error hagánmelo saber pr facebook, porque no probé ninguno d estos cmando solo lei lo que hacian

### Links Importantes
* Documentacion git (http://git-scm.com/docs/)
* Más sobre git (http://gitref.org/basic/)
* Sobre la mala practica de git push y como solucionarlo (http://longair.net/blog/2009/04/16/git-fetch-and-merge/)