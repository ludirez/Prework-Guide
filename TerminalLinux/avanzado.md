Comandos avanzados de la terminal de Linux.
	se pueden usar también en WSL

## comunes
	$ echo "cosa de salida"			->genera un standard Output de cualquier cosa que le pasemos
	$ less [archivo]				->para explorar el contenido de un output
	$ cat [archivo1] [archivo2]		->para concatenar varios output



## pipe operator
	permite que el standard output se convierta en el standard input de otro comando.
	entiéndase: que lo que vota un comando(output) se le pasa a otro como input para que haga algo más
	$ ls -lh | less		mostrará el ls dentro del comando less
	$ ls | sort | tee archivosHome.txt		->"sort"ordena alfabéticamente una salida. "tee" Crea un archivo en base a una entrada



## Wildcards
	serie de caracteres especiales que nos permiten realizar patrones de búsquedas.

	1.- << * >>  asterisco	
		ls *.txt		mostrará documentos de extensión .txt ->funciona con cualquier extensión

		ls búsqueda*	mostrará archivos que contengan la palabra búsqueda ->funciona con cualquier palabra

		ls -d [[:upper:]]*		mostrará directorios que inicien en mayúsculas. -d define que solo busque en 2 niveles.

		ls -d [[:lower:]]*		lo mismo pero minúsculas.

		ls [a]*			mostrará directorios que contengan una "a"

		mv *.txt directorio/		moverá todos los .txt a donde le estas indicando funciona también con cp y rm

		$ wc -l/-w/-c movies.csv		"word Count" cantidad de lineas tiene, cuantas letras tiene, numero de bits

## Re direcciones

## Link simbólico
	tipo de archivo que hace referencia a alguna ruta. Comandos que configuramos para ejecutar una linea de código mas larga a través de un comando mas corto.

		ln -s usuario/ruta/deseada  NombreDeReferencia
		cd NombreDeReferencia

## Variables de entorno VDE
	$ printenv					->lista de todas las variables configuradas

	$ echo $NombreVDE		->echo para mostrar lo que contiene la variable

	$ cd $HOME					->Ejecutara la rota que haya en la variable HOME

	$ echo $PATH				->Todas las rutas de los binarios que ejecuta el SO. hay vases que hay que agregar manualmente cosas a esta variable para que se puedan ejecutar.
		para modificar:
			$ ls -la			-> buscar directorio .bashrc(enLinux)
			$ code .bashrc		-> abrirá el documento para modificar 
				en el editor:
					PATH=$PATH:/home/usuario/carpeta

## Alias y atajos configurados en el .bashrc
	## alias
	alias L='ls -lha'
	alias holis='sudo apt update'
	alias chau='sudo apt upgrade'

	##variables
	mensajeee='Hola Mundo'
	$ echo $mensaje		->imprime el 'hola mundo en la terminal'


## Comando de Búsqueda

	para buscar elementos.

	1.- which		busca la ruta de los binarios (programa ejecutable) en el PATH 
		$ which code		code de VS code, mostrara el pwd de el binario 
	2.- find			buscar desde donde le digas, lo que le digas:
			Segmentar por nombre -name
			$ find ./ -name file	->buscará todos los archivos que contengan "file" en el nombre desde el home "./"
			$ find ./ -name *.txt | less	buscará todos los .txt y se pararan por un less para leerlo mejor

			Segmentar por tipo -type
			$ find ./ -type d,f,l -name 'nombre'	->buscará por directorio 'd' ó files 'f' ò enlaces simbólicos 'l'; por el 'nombre sin comillas'. 
			$ find ./ -type f,d -name "D*"			la coma ',' concatena métodos de búsqueda. D* buscara todos los que empiece con D mayúscula. 

			Segmentar por tamaño -size
			$ find ./ size 4k/-4M/+4k	'k' de kilobyte 'M'Megabytes

			Buscar vacíos -empty
			$ find ./ -type d -empty		Por ejemplo, si quisiera buscar todas las carpetas vacías

	3.- Limitar la búsqueda (-maxdepth -mindepth)
$ find ./ -type d -maxdepth 2 | less		buscará hasta un máximo de 2 niveles de profundidad. se recomienda pasarlo por less.
$ find ./ -type d -mindepth 1 | less		buscará a partir de 2 niveles de profundidad

ejercicios:
1.-Busca tus archivos mayores a 100Mb, con una profundidad máxima de 4, que comiencen por la letra d
	$ find ./ -maxdepth 4 -type f -size +1000k -name 'd*' | less

2.-Busca todos los Archivos .log
	$ find ./ -type f -name *.log

3.- busca todos los txt y mételo en un archivo e imprime un mensaje
	$ find ./ -name '*.txt' > text_docs.txt && echo "Files saved successfully"

	4.- grep		“Grep” significa Global Regular Expression Print, para buscar texto dentro de un archivo.
					grep [ExpresiónRegular] [archivoDondeBuscar]
			$ grep Towers movies.csv		Buscará match con la palabra "Towers"
			$ grep the movies.csv			Buscará match con la palabra "the"
			$ grep -i the movies.csv | less		Buscará match con la palabra "the" ignorando con "-i" si es mayúscula o minúscula. se puede pasar por less
			$ grep -c the movies.csv		"-c" hace de contador para la palabra que se busque "the".
			$ grep -ci the movies.csv		se puede concatenar con otro parámetro de búsqueda
			$ grep -vi towers movies.csv > sonTowers.txt		"-v" buscara las que NO contengan "towers", adicionalmente se puede enviar el output a un archivo

## Utilidades de RED
	$ ifconfig					información de tarjeta de red y más
	$ ip address
	$ ping -c 4 www.google.com		"-c 4" limita las peticiones a 4. control+C para para la ejecución
	$ ping -s 20 www.google.com		Para hacer pruebas con paquetes de 20 bytes escribimos:
	$ curl www.google.com > index.html 		trae un archivo a manera de texto y lo podemos enviar a un archivo.
	$ wget www.google.com		trae directamente el html de la pagina que le pasemos. mejor formateado de que curl
	$ traceroute www.google.com		indica todos "los pc" por donde pasa mi petición antes de llegar a google.
	$ netstat -i				indica especificaciones de hardware de red

## Compresión de Archivos en .tar y .zip
	$ tar -cvf comprimir.tar comprimir
		"-c" para comprimir
		"v" para que sea visual,
		"f" indicando que va a comprimir un file
		"comprimir.tar" el nombre y extension con la que a a quedar el archivo
		"comprimir" el nombre del file que se va a comprimir

	$ tar -cvzf comprimir.tar.gz comprimir
		"z" estará dando mejor calidad de compresión
		".gz" ahi que añadirlo para que "z" funcione
	
	# ver el contenido sin descomprimirlo
		$ tar tvf archivo.tar

	# descomprimir .tar
		$ tar -xzvf comprimir.tar.gz
			"-x" para descomprimir
	
	$ zip -r comprimirConZip.zip comprimir
	$ unzip comprimirConZip.zip

## Manejo de Procesos
	$ ps		muestra los procesos que están corriendo en la bash
				PID proses ID
	$ kill 		para terminar proceso. hay que buscar la manera correcta de usarlo
		$ pkill firefox Acabas con el proceso usando el nombre en lugar del id
		$ killall -nombre_del_proceso		para acabar con todos los procesos que coincidan con el nombre o el id.
		$ kill -9 pidNum		es el identificador numérico del proceso
		$ kill -9 processName	nombre del proceso
		$ kill -9 PNAME			nombre del proceso que se quiere eliminar que puede ser una expresión regular


	$ top		lista de procesos que san usando mas recursos.
				presionar la tecla "h" mostrará las opciones de filtrado
				ctrl+c cierra top
	$ htop		hyper top.. mejorado, mas musculo y más pelos.

	ejercicio.
	ejecuta car & ls en la terminal
	visualiza el proceso en ps
	enséñame a matar el proceso con kill. =D

	Enviando procesos al background(proceso en segundo plano) y devolverlos al foreground (trabajo en pantalla)
		$ cat > unaNota.txt		escribimos texto y
			ctrl+D		para terminar la edición
			ctrl+Z		para pausar el programa y dejar este cat en el background de procesos
		$ jobs		para consultar que procesos tenemos en background. [n] describe la posición del proceso
		$ fg [n]	para traerlo de vuelta
	si ejecutas un proceso que no te deja usar la terminal, hacemos ctrl+Z para pausarlo.
	con jobs veremos el [n] del proceso, procedemos a ejecutar 
	$ bg [n]	asi haremos que el proceso siga en segundo plano y deja la terminal libre.

## Editores de texto en la terminal
	VIM
	NANO
	Emacs

## Personalizar la terminal de comandos
	