desde Ubuntu.
en la carpeta de trabajo, en la consola: 

configuracionde git, 00nombre de usuario
git config          ->lista de loq ue se peude configurar
git config --list
git config --list --show-origin --->para mostrar ususario configurado

    1.-verificar nombre de usuario.
        en la terminal: git config --global user.name "nombredeusuariogithub" (incluye comillas)
    2.-verificar correo de usuario.
        en la terminal: git config --global user.email "correoelectronicoregistradoengithub"
    3.-verificar que quedo configurado
        en la terminal: git config --list



rama master
git init                            ->inicia seguimiento de cambios

git status                          ->Muestra que hay para sincronizar con git
                                        mostrara en rojo los pendientes

git add "archivo.extencion"         ->para agregar a cache, el archivo al paquete a sincronizar
                                        mostrara en verde los enlistados een chache

git rm --cached "archivo.extencion"          ->para quetar de la lista mas no borra el archivo del dir

git commit -m "mensaje descriptivo"            ->para subir los enlistados en cache y dejar un
                                                aviso descriptivo de que va o que se hizo

Para despues de cambios en 1 o mas archivos, se deve volver a ahcer el "git add"
pra agregar todos los archisvos cambiados, 
    en consola: git add .    ->donde el "." indica todo dentro del dir

git log "archivo.extencion"  -->mostrara el historial de cambios de el archivo.

mas comandos:
git show "archivo.extencion"  ->sin coillas, mostrara lo que s e ha cambiado

git diff "dumero del comid a" "numeor de comit b"   ->compara a vs b

cada commit es una version de el archivo. con "checkout" se trae devuelta la vercion que encesitesmos con en codigo de numeros largos de cada log. ejemplos proximos

Ramas del proyecto.
    "master" que ahora se llama "main" es la principal
    "development" para probar cosas
    "bugfinxing" llamado ahora "hotfix" para arreglos urgentes
pueden haber muchas mas ramas, lo importante es aprender a hacer "merge" que es la union de las ramas  alternar con al sagrada linea del tiempo principal.

    Volver en el tiempo.
git log                     nos mostrará  todos los comid, selecionamos a donde queremos ir.
                            nos apoyaremos en los mensajes. pore so su importancia.
                            selecionamos el NunCommit al que queremos voler

git reset nunCommit --hard   para volver la la version selecionada y se pierde lo que precedia
                            al NumCom|mit

git reset nunCommit --soft   por definir

se creo una caprta con un html y un css, y cambiamos el nombre de un archivo texto.txt a historio.txt apra hacer el ejercicio de solo volver a historia.txt a si nombre anterior.

git log --stat      para ver exactamente que se ha cambiado en cada commit

git checkout NumCommit "archivo.extencion"      nos mostrará el archivo que solicitemos a su status que se
                                                encontraba en el NumComiit que le pasamos.
    en mi ejemplo, antes del ejercicio, cambie el nombre del archivo. 
    intentare llamarlo con su nombre actual. 
    no funciono. huvo que llamarlo por su antiguo nombre
    al traerlo con el nombre antiguo, se me generaron 2 archivos en el workspace. el primero que mande a  llamar y el mas reciente con otro nombre. entonces, averiguar que aplicaciones se le puede dar a este bug.

git checkout master "archivo.extencion"         nos traera de regreso la version ams reciente. simpre y cuando no se ahya hecho 
                                                un reset --hard y como el ejemplo pasado, no se le haya cambiano el nombre al archivo

nota importante explicativa
```html
    <a href="/comando rm en git.md"></a>
```
Mas Comandos:

git commit -am  "mensaje descriptivo"    ->hara un "add ." y un "commit" en un solo paso. simpre y cuando no se hayan creado nuevos archivos
