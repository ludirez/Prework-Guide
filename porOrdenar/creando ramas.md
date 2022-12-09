1r.- actualizar el repositorio local

    Modo A:
        git add .
        git commit -m "mesaje descritivo"
    
    
    Modo B: funciona simpre y cuando se modifiquene xistenten pero no se creen nuevos archivos
    git commit -am "mensaje descrptivo"
    o
    git commit -a (enter) se despara entorno para escribir mensaje
        esc+i apra empezar a escribir
        Esc+shiff+zz para guardar y salir
    
    git log para ver los cambios
    git log -stat para ver ams detalles
    git show mostrara detalles de los cambios realizados
    
    ----> LETRA Q PARA SALIR <--------------

2do, Ceando rama
    git branch "nombre de la rama"  ->sin comillas, crea rama
    git branch -M "newname" --> renombra la rama..
	
3ro. git checkout "nombre de rama"  ->para desplasarse entre ramas
	git branch  ->para ver todas las ramas y saber en cual estoy
