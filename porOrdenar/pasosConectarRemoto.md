conectar con servidor remoto.

Modo 1 HTPPS
	Registrate en github
	ir a repositorio
	crear un nuevo repositorio: nombrar y escribir descripcion.
	elejir publico o privado
	crear archivo README.TXT
	aun no agregar licencias.
	Clone o Download y elegir SSH
	vamos decirle a git que vamos a agregar un origen remoto
		git remote add origin git@github.com:xxx.git (lo da hithub)
		git remote  -->mostrata doden estamos ahora
		git remote -v ->muestra mas info. rutaa para hacer Fetch y Push
	Rwcordemos que cambiamos el nombre de la ramna master a main con git branch -m "newName"
		git push -u origin main		->mandara rama main del local a origin del remoto
para cambiar el origen puedes:
1.-revisar el origen configurado con
		git config --list
2.-para Sobreescribir el origen:
		git remote set-url origin git@github.com:xxx.git

puede que de coflicto  si tienes el deadme o almos mas en el repo donde vas a subir,
entonces debes bajar al repo local loq ue tegan en el remoto para asi se sincronice 
y olver a ahcer el push sin problemas.
	
