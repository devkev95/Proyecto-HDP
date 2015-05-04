Branch donde vamos a subir todo lo relacionado al codigo del lado servidor

#### En este archivo les voy a poner algunas instrucciones para ir trabajando con git
Nota 1: El archivo solo se ve correctamente en GitHUB, asi que no se preocupen que si lo descargan se vea un solo deschonge :laughing:

Nota 2: Estos pasos son para Linux, pero supongo que pueden servir de idea de que se debe hacer en Windows

Nota 3: El archivo irá agregando mas tips segun necesitemos

## Instrucciones para el clonado y correcta sincronización de nuestro repositorio local con el repositorio en GitHUB:

1. Primero es importante clonar este repositorio, para esto es necesario colocarte dentro de una carpeta de su elección y ejecutar el siguiente comando en consola:
	```console
	git clone https://github.com/devkev95/Proyecto-HDP
	```
	Creo que el comando se explica solo 

2. Git automaticamente creará una carpeta donde se encontrarán los archivos de la rama principal de nuestro repositorio, BackEnd.

3. En linux hay un problema cuando se descargan repositorios(Al parecer en windows también existe este problema); git no crea localmente las demas ramas excepto la principal, en nuestro caso BackEnd, asi que hay que crearlas. Para esto ejecutamos el siguiene comando en consola:
	```console
	git checkout -b Reglas origin/Reglas
	```
	Un poco de explicación del comando anterior:
	El comando  checkout sirve para moverte de una rama a otra; si ejecutan este comando, bueno al menos en linux si sucede, verán que los archivos en la carpeta local del repositorio cambiarán de los de la rama anterior a la nueva rama a la cual se han movido. El modificador -b del comando checkout crea la rama que le digamos, en este caso Regla, antes de moverse a ella; osea que en este comando estamos creando y moviendonos a la rama que acabamos de crear al mismo tiempo, por separado se puede realizar de la siguiente forma: 
	```console  
	git branch Reglas 
	``` 
	y luego

	```console  
	git checkout Reglas 
	``` 
	La última parte del comado es una especie de link, linkea nuestra rama actual con la rama del repositorio; por lo tanto cualquier cambio que realizamos en la rama local se vera reflejado en nuestro rama en el repositorio(Explicaré como se hace esto luego). Por lo tanto, para crear a linkear nuestras ramas locales tenemos que realizar este proceso para las ramas Reglas(si no la han creado y linkeado ya), Documento_Escrito y GUI. Por ejemplo: cambiando Reglas por Documento_Escrito y origin/Reglas por origin/Documento_Escrito.

P.D : Mañana extenderé mas el archivo con la explicacion de como realizar cambios en nuestro repositorio y que se vean reflejados en el repositorio web.