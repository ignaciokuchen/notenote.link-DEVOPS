### Copy copio el codigo
### Modify modifico el codigo 
### Merge fusionar el codigo

## Comandos
 git ver => vemos la version 
 git help
 
 git 
git add . => agrego al mapeo del repositorio git todos los archivos de donde estoy parado

git commit -m "Mensaje a enviar" => subo el archivo a a memoria y lo preparo para subirlo
git commit -a -m "Mensaje a enviar" => hace un commit y un push 
git push => me confirma la escritura en el repositorio.
git push -u origin master => subimos al repositorio on-line 
git status => comparamos nuestro codigo con el remoto 
git pull => nos trae los cambios del repositorio 
git log => nos pasa un historial de los commits 
git reset --hard "commit" => revierte el codigo a como estaba justamente despues del commit indicado con el hash. 
git reset --hard origin / master => Revierte el codigo en la nube/servidor productivo
git branch=> para ver en que rama estamos parados, o trabajando actualmente. 
git checkout -b "nombre de la nueva rama"  => Creamos una nueva rama
git checkout "nombre rama" => Cambiamos de rama
git merge "nombre de la otra rama" => aqui le indicamos el nombre de la rama de la cual queremos traer el codigo, y fusionarlo a la rama donde estamos parados. Por lo general lo queremos fucionar a master, por lo que previamente recorda revisar en que rama estas (si deseas fusionarlo a master, primero parate en esta rama). 


