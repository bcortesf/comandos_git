
https://docs.github.com/es/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax

https://programminghistorian.org/es/lecciones/introduccion-a-markdown

#  …or create a new repository on the command line
```
  echo "# BCgit" >> README.md
  git init
  git add README.md
  git commit -m "first commit"
  git branch -M main
  git remote add origin  https://github.com/OrganizacionBCF0/BCgit.git
  git push -u origin main
```

#  …or push an existing repository from the command line
```
  git remote add origin https://github.com/OrganizacionBCF0/BCgit.git
  git branch -M main
  git push -u origin main
```
# ####################################################################
# ####################################################################

#  Clonar proyecto
> git clone https://github.com/OrganizacionBCF0/flujo-git.git

#  *Entrar a carpeta del proyectoGit y abrir nuestro editorPreferido de codigo. Abrir vsCode:*
> code .

#  Agregar por carpeta ó archivo especifico (nombreArchivo.extension), según "git status"
```
  git add miCarpeta
  git add cliente.java
```
#  Agregar todos los archivos y carpetas al .gitLocal, según "git status"
> git add .

# ____________IMPORTANTE____________
##  *NOTA: Cada archivo en local, agregado por "git add", seran subidos a un STAGGIN-AREA, de .gitLocal*
###  STAGGIN-AREA: Espacio de memoria temporal, que esperan tener un comentario asociado "commit"

#####  Ver archivos pendientes en local, sin commit.
    - (verde): agregadoCompleto
    - (rojos): SinAgregar    ó    sinAgregarConModificacionesPendientes
> git status


* TIPOS DE COMMIT
  * git commit     : (por consola de visualCode)
  * git commit -m  : (solo comentario, LOS ARCHIVOS DEBEN ESTAR GIT ADD nombre.ext)
  * git commit -am : (comentario y agrega de forma automatica)

# --------------_____--------------
# ____________IMPORTANTE____________
#  Crear commit asociado a mis archivos
> git commit
  ## Se abre una terminal dentro de visualCode, LUEGO SEGUIR PASOS:
      1. Escribir nuestro comentario
      2. Guardar con comando  CTRL + S
# --------------_____--------------

#  Ver mis (commit's) en forma de comentario que tenga creado, en STAGGIN-AREA .gitLocal
  - Muestra UN parametro  :  (HEAD->main)              mi comentario
> git log

# Verificar que no existan cambio en el repositorio web_GitHub
> git pull


#  Guardar (El comentario + archivos) de mi rama en repositorio: web_GitHub "git push origin rama123"
> git push origin main
#  Comprobar guardado en web_Git_Hub, deberia aparecer dos parametros:
  - Muestra DOS parametroS:  (HEAD->main, origin/main) mi comentario
>git log



# ###########################################################################
# ###########################################################################

#  Como trabajar con 2 o mas remotos
## Listar urlRemotas de mi repositorio
> git remote -v
##  Agregar remotos
> git remote add empresa https://github.com/OrganizacionBCF0/BCgit.git
##  Eliminar remotos
> git remote remove empresa


#         RAMAS
## Listar ramas gitLocales
> git branch
## Listar ramas gitRemotas
> git branch -r
## Listar ramas gitLocales y gitRemotas
> git branch -a


##  Eliminar ramaLocal, en FORKcopia    &&    Eliminar ramaRemota, en FORKcopia
> git branch -D <rama123>
> git push origin --delete <rama123>
##  Eliminar ramas:  ramasLocales && ramasRemotas
> git branch -D <rama123> <rama456>
> git push origin --delete <rama123>
> git push origin --delete <rama456>


#  Cambiar de ramaA ---> a una ramaB (cualquira de los dos)
>  git checkout <nombreRama>
>  git switch <nombreRama>
#  Crear rama y pararse en ella (cualquier de los dos comandos)
>  git branch -M develop
>  git checkout -b develop
#  Enviar rama creada en gitLocal a webGitHub
>  git push origin develop


...
#### https://youtu.be/CNXPHpvzwTA?list=PLTeHAfkP0LymcnE6sJuEQ2Ghl7UskDuzw&t=409
#  Agregar la urlRemota del proyecto original, dentro de un FORK-proyectoCopia.
   Para que FORK<urlRemota>, pueda mapear las ramas de urlRemotaProyectoOriginal
   EJEMPLO: (urlOrganizacion,  urlFORKcopia)
     - https://github.com/OrganizacionBCF0/BCgit.git
     - https://github.com/BryanCFz/BCgit.git
     git remote add <nombreRemoto>
>  git remote add empresa https://github.com/OrganizacionBCF0/BCgit.git

#  Al mostrar las urlRemotas nos quedaria la (original y empresa)
   EJEMPLO:
     empresa https://github.com/OrganizacionBCF0/BCgit.git (fetch)
     empresa https://github.com/OrganizacionBCF0/BCgit.git (push)
     origin  https://github.com/BryanCFz/BCgit.git (fetch)
     origin  https://github.com/BryanCFz/BCgit.git (push)
>  git remote -v

#  Si quiero editar el nombre o url, se elimina urlREmota(empresa) y se crea de nuevo.
>  git remote remove empresa


...    ...    ...    ...
# PASOS PARA ABSORVER UNA RAMA NUEVA DE (ProyectoOrganizacion), QUE NO EXISTE EN EL FORKcopia
##  Desde FORK-copia "https://github.com/BryanCFz/BCgit.git". Se comprueba si alguna ramaRemota del
   proyectoOrganizacion tuvo cambio, si hay cambio la descarga pero en la CACHE y se mostraran en listado
>  git fetch empresa
##  Las ramas quedaran descargadas solo en CACHE, y las podemos ver despues del FETCH
>  git log
##  Para absorber a nivel local, la nueva ramaRemota del proyectoORIGINAL que no tenemos,
   la absorbemos como una ramaLOCAL asi:
>  git checkout -b dev
##  Comprobamos la descarga ramaLocal en proyecto FORKcopia
>  git branch -a
##  Por ultimo subimos esta ramaLocal a nuestro repositorio FORKcopia, haciendo push
>  git push origin dev


...    ...    ...    ...
# PASOS PARA ABSORVER UNA RAMA EXISTENTE DE (ProyectoOrganizacion), QUE EXISTE EN EL FORKcopia, PERO LE FALTAN LAS ACTUALIZACIONES
##  Verifico urlRemota y la comparo con la lista ramasRemotas
>  git remote -v
>  git branch -a
##  Absorver ramaRemota de proyecto Original , en una ramaLocal para proyecto FORKcopia
>  git pull empresa dev
##  Actualizar cambios de  FORKcopia<ramaLocal> a la FORKcopia<ramaRemota>
>  git push origin dev


...    ...    ...    ...
...    ...    ...    ...
# PASOS PARA SABER SI ESTOY SINCRONIZADO DE  A NIVEL
  DEL (ProyectoOrganizacion) RAMAS-LOCALES Y RAMAS-REMOTAS
  EN MI FORKcopia, PERO LE FALTAN LAS ACTUALIZACIONES
  1. Revisar de forma manual las ramas
  2. Obtener la sincronización
  3. Volver a revisar de forma manual las ramas esten todas sincronizadas
  4. Actualizo mi FORK.copia a la mas actual de proyectoORGANIZACION
>  git log --oneline --all
>  git fetch empresa
>  git log --oneline --all
>  git pull empresa ramaDev

##  B
>  git ?



...    ...    ...    ...
...    ...    ...    ...
#   Al terminar una actividad FORKcopia<rama123>, con pullRequest hacia proyectoORGANIZACION, eliminar la FORK<rama>
##  Eliminar ramaLocal, en FORKcopia
> git branch -D <ramaDev>
##  Eliminar ramaRemota, en FORKcopia
> git push origin --delete <ramaDev>


...    ...    ...    ...
# Si soy administrador, aprobador de codigos de mis desarrolladores
##  AL enviar desde FORK.copia la ramaRemota<rama123> con pullRequest, que apunta a la ramaRemota<dev> del proyectoORIGINAL
   despues de testear todo en ramaRemota<dev>. Ahora desde proyectoORIGINAL absorvemos para produccion.rama<main>,
   esa rama<dev> con una mezcla.
   Debemos pararnos en produccion rama<main>
> git switch main
> git merge <ramaDev>
> git push origin <ramaMaster>


...    ...    ...    ...
#  Navegar entre commits
##  Obtener "idCommit"   (cualquier de los dos)
> git log --oneline --all --graph --decorate
> git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
##  Navegar al commit
> git checkout <idCommit>
## Devolverse al inicial  (cualquiera de los dos)
> git checkout <ramaDev>
> git checkout <rama123>



...    ...    ...    ...
#  CREACION DE TAGS O ETIQUETAS("release"):
### usadas para versionar rama<MasterMain>, EJEMPLO: Lanzar en produccion una version de proyecto
##  Crear version tagLocal, para ramaLocal
>  git tag "v0.0.1"
##  Consultar tag de ramaLocal
>  git log --oneline --all
##  Mostrar archivosTagsNombresLocales creado, asociado a ramaLocal
>  ls .git/refs/tags/
##  ver contenido archivoTagLocal, asociado a ramaLocal
>  cat .git/refs/tags/<archivoTagNombre>
##  Eliminar archivoTagNombreLocal, asociado a ramaLocal
>  rm .git/refs/tags/<archivoTagNombre>

##  Subir tagLocal al repositorio version.tagRemoto (OJO: estar enb rama<main>)
git push origin --tags


...    ...    ...    ...
##  Verificar informacion de remoto(ProyectoOriginal) a --> remoto(FORKcopia): Si tiene algo lo muestra
###  "DESDE     FORKcopia"
>  git fetch empresa
##  Siempre revisar que todo este sincronizado, ramasLocales y ramasRemotas
>  git log --oneline --all
## De contrario traer cambios de proyectoORIGINAL
>  git pull empresa main
## actualizar ramaRemota de FORKcopia
>  git push origin master
# STASH:  (Guardar codigo de forma temporal)
##  Ejemplo: Estoy parado en "ramaEtiquetas", y guardamos ese codigo temporal (SIN HACER COMMIT)
##  {{PASO-1}} = guardar en una hoja el <<idStash>>
>  git stash
## Una vez guardado el codigo de "ramaEtiquetas" en mi STASH, me paso a la principal "ramaMaster", creamos otra nueva rama
## para hacer cambios en ella "ramaStash"
>  git switch main
>  git branch ramaStash
>  git checkout ramaStash
## Hago cambios con commit y los subo a ramaRemota
>  git status
>  git commit -am "En 'ramaStash'; Tutorial de codigo usando STASH, pendiente volver al codigo 'ramaEtiquetas'"
>  git push origin ramaStash
#### *REALIZAR PULL-REQUEST DE  "ramaStash"*		            ***  ***  ***
##  Reviso gitHub y veo "ramaStash", reviso ramas y apareceran dos "ramaEtiquetas" y "ramaStash"
##  Nos devolvemos a la inicial "ramaEtiquetas", vemos que no tenemos cambios con status
##  Entonces debemos restablecer nuestros cambios
>  git branch
>  git switch ramaEtiquetas
>  git status
##  Listamos los stash guardados , mostrara dos items: (posicionStash{0}, <<idStash>>)
##  <<idStash>> corresponde al del {{PASO-1}}
>  git stash list
##  Restauramos nuestro STASH de codigo temporal en la ramaEtiquetas y verificamos
>  git stash pop
>  git status
>>>>  git add .... git commit .... git push origin ramaEtiquetas >>>>
#### *REALIZAR PULL-REQUEST DE  "ramaEtiquetas"*
		            ***  ***  ***
##  SOLO-DESDE-ADM: Github(proyectoORGANIZACION) mostrara dos "ramaEtiquetas" y "ramaStash"
    1. Aceptamos el pullRquest del stash ramaStash
    2. Aceptamos el pullRquest del stash ramaEtiquetas

##  Eliminar mis ramasLocales y ramasRemotas
>  git branch -D <ramaStash> <ramaEtioquetas>
>  git push origin --delete <ramaStash>
>  git push origin --delete <ramaEtioquetas>
##  Actualizacion FORKcopia.rama<master>
  1. Revisar de forma manual las ramas
  2. Obtener la sincronización
  3. Volver a revisar de forma manual las ramas esten todas sincronizadas
  4. Actualizo mi FORK.copia a la mas actual de proyectoORGANIZACION
>  git log --oneline --all
>  git fetch empresa			    :Sincronizar mi ramaMASTER."idCOMMITS", com el de proyectoORGANIZACION
>  git log --oneline --all	  :revisar sincronizaciones
>  git pull empresa dev       :Bajar el codigo proyectoORGANIZACION<ramaMaster> a mi FORK.ramaLOCAL<main>
>  git push origin master		  :subir codigo FORKramaLOCAL<main> al --> subir codigo FORKramaREMOTO<main>
### CASO ESPECIAL (2 RAMAS EN PARALELO Y UNA DE ELLAS CON "STASH")
  1. FORK: Crear ramaStash, hacer codigo (sin agregar a WORKING-DIRECTORY, sin commit), y guardarlo en STASH
    ```
    git switch main
    git branch -M ramaStash
    git stash
    ```
  2. FORK: Crear ramaEtiquetas, hacer codigo (agregar a WORKING-DIRECTORY, commit)..., pull request
    ```
    git switch main
    git branch -M ramaEtiquetas
    git commit-am "Se agrega tutorial etiquetas"
    git push origin etiquetas
    ```
    *{GITHUB}.PULL-REQUEST:  {proyectoOGANIZACION<dev>} <= {FORK<ramaEtiquetas>}*
  3. FORK: Restablecer STASH ramaStash, add WORKING-DIRECTORY, commit, pull request
    ```
    git switch ramaStash
    git stash list
    git stash pop
    git commit -am "tutorial codigo STASH"
    git push origin ramaEtiquetas
    ```
  4. proyectoORGANIZACION{GITHUB}:  pull-request "ramaStash", aceptar y en boton<merge>
    *{GITHUB}.PULL-REQUEST:  comentario, aceptar*
    - proyectoORGANIZACION{GITHUB}:  pull-request "ramaEtiquetas", ERROR MERGE, POR TOCAR MISMO ARCHIVO
  5. FORK: solucion uso de merge, solucionar conflicto manual y (add+commit)
    ```
    git switch main
    git fetch empresa         :sincronizar rama y idCommits
    git pull empresa dev      :Traer codigo actualizado
    git switch ramaEtiquetas
    git merge main
    git commit -am "solucion conflicto merge RamEtiquetasRamStash"
    git push origin ramaEtiquetas
    ```
  6. Actualizar ramaMaster con los pasos encima de estos pasos con el subtitulo "Actualizacion FORKcopia.rama<master>"


...    ...    ...    ...


...    ...    ...    ...














...    ...    ...    ...    ...    ...    ...    ...    ...    ...    ...    ...
# xxx
> git ?

## Descarga cambios de repositorioRemoto en CACHE && crea ramaLocal y se posiciona en ella
>  git fetch && git checkout develop
>  git fetch && git checkout rama-123

## Guardar "stash", cambios de un desarrollo , para hacer los pasos:  1.guardar en stash, 2.hacer pull, 3.restablecer stash
> git ?
## Resolver Conflictos , hacer merge (marcando resultos los arreglados) y subir cambios
> git ?
## Quitar archivos del STAGGING-AREA, antes de hacer un push
> git ?
## Revertir un commit que ya fue enviado por push
> git ?
## Editar el mensaje de un commit, antes de hacer un push
> git ?
## Navegar entre comits de web_GitHub
> git ?
