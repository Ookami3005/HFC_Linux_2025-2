# Cheatsheet Linux
## Codificaciones y compresiones
### Codificaciones

- **Codificar base64**: `base64 archivo.txt` o `cat archivo | base64`
- **Decodificar base64**: `base64 -d archivo.txt` o `cat archivo | base64 -d`

- **Codificar base32**: `base32 archivo.txt` o `cat archivo | base32`
- **Decodificar base32**: `base32 -d archivo.txt` o `cat archivo | base32 -d`

- **Codificar hexadecimal plano**: `xxd -p archivo.txt` o `cat archivo | xxd -p`
- **Decodificar hexadecimal plano**: `xxd -p -r archivo.txt` o `cat archivo | xxd -p -r`

- **Codificar/Decodificar Rot13**: `cat archivo | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'` o `cat archivo | rot13` o `rot13 archivo`
- **Codificar/Decodificar Rot47**: `cat archivo | tr '!-~' 'P-~!-O'`

### Compresiones

- **Comprimir zip**: `zip -r comprimido.zip carpeta/` o `zip comprimido.zip archivo`
- **Descomprimir zip**: `unzip comprimido.zip`

- **Comprimir gzip**: `gzip archivo` o `gzip carpeta/`
- **Descomprimir gzip**: `gzip -d archivo.gz`

- **Comprimir bzip2**: `bzip2 archivo` o `bzip2 carpeta/`
- **Descomprimir bzip2**: `bzip2 -d archivo.bz`

- **Comprimir tar**: `tar -cf comprimido.tar archivo1 archivo2 ... archivoN`
- **Descomprimir tar o tar.gz o tar.xz**: `tar -xf archivo.tar`

## Manipulación y formateo de información

### Filtrado de información
- **Primeras líneas**: `head archivo` o `cat archivo | head`
- **Últimas líneas**: `tail archivo` o `cat archivo | tail`
- **Cadena**: `grep cadena archivo.txt` o `cat archivo | grep cadena`
- **Expresión regular**: `grep -E patron archivo.txt` o `cat archivo | grep -E patron`
- **Busqueda inversa**: `grep -v cadena_no_deseada archivo.txt` o `cat archivo | grep -v cadena_no_deseada`

### Manipulación y formateo
- **Extraer campos**: `cut -d : -f 1 archivo.txt` o `cat archivo | cut -d : -f 1`
- **Remplazar caracteres** : `cat archivo | tr 'c' 'a'` o `cat archivo | tr 'a-z' 'A-Z'`
- **Remplazar patrones** : `sed -e 's/patron/remplazo/g' archivo.txt` o `cat archivo | sed -e 's/patron/remplazo/g'`

- **Enumerar líneas de un archivo**: `nl archivo` o `cat archivo | nl`
- **Ordenar las líneas de un archivo**: `sort archivo` o `cat archivo | sort`
- **Eliminar líneas repetidas *adyacentes***: `uniq archivo` o `cat archivo uniq`
- **Mostrar únicamente líneas que no se repitan**: `sort archivo | uniq -u`
- **Mostrar únicamente líneas que si se repitan**: `sort archivo | uniq -d`

## Redirecciones y operadores

### Redirecciones
- **Redirección de entrada estándar**: `comando < archivo`
- **Redirección de salida estándar**: `comando > archivo`
- **Redirección de errores**: `comando 2> archivo`
- **Tubería**: `comando | comando`

### Operadores
- **Último comando ejecutado**: `!!`
- **Secuencia de comandos**: `comando ; comando`
- **Secuencia de comandos *en caso de éxito***: `comando && comando`
- **Secuencia de comandos *en caso de error***: `comando || comando`

## Instalaciones
### Gestor de paquetes

- **Busqueda en repositorios**: `apt search <nombre>` o `dnf search <nombre>` o `pacman -Ss <nombre>`
- **Instalación desde repositorios**: `sudo apt install <nombre>` o `sudo dnf install <nombre>` o `sudo pacman -S <nombre>`
- **Desinstalación de paquetes**: `sudo apt remove <nombre>` o `sudo dnf remove <nombre>` o `sudo pacman -Rns <nombre>`

### pipx
- **Instalación por pipx**: `pipx install <nombre>`
- **Desinstalación por pipx**: `pipx uninstall <nombre>`

### Enlace simbólico
- **Crear enlace simbólico**: `sudo ln -sf /ruta/archivo/real /ruta/enlace/creado`

## Redes
### Básicos
- **Ping**: `ping <IP>`
- **Trazado de paquetes**: `traceroute <IP>`
- **Interfaces de red, direcciones IP asignadas y demás**: `ifconfig`

### Interacción con puertos
- **Abrir un puerto de tu dispositivo**: `nc -lnvp 9000` o `ncat -lnvp 9000`
- **Conectarse a un puerto de un dispositivo**: `nc <IP> <puerto>` `ncat <IP> <puerto>`
- **Iniciar una conexión SSL**: `ncat --ssl <IP> <puerto>`

### Web
- **Imprimir código fuente de una URL**: `curl https://url.com`
- **Descargar código fuente de una URL**: `wget https://url.com`

### SSH
- **Conectarse normalmente**: `ssh usuario@dominio` o `ssh usuario@ip`
- **Conectarse con archivo llave**: `ssh usuario@dominio -i llave` o `ssh usuario@ip -i llave`
- **Ejecutar comando al conectarse**: `ssh usuario@dominio 'sh'` o `ssh usuario@ip 'sh'`

## Usuarios, Grupos y permisos

### Usuarios
- **Crear un usuario con directorio hogar y shell**: `sudo useradd -m -s /usr/bin/zsh ookami`
- **Modificar la shell de un usuario**: `sudo usermod -s /bin/bash ookami`
- **Eliminar un archivo y su directorio hogar**: `sudo userdel -r ookami`
- **Agregar un usuario a los grupos secundarios grupo1 y grupo2**: `sudo usermod -aG grupo1,grupo2 ookami`

### Grupos
- **Crear un grupo con usuario1 y usuario2**: `sudo groupadd -U usuario1,usuario2 hfc`
- **Agregar usuarios a un grupo existente**: `sudo groupmod -U usuario1,usuario2 grupo_existente`
- **Eliminar grupo**: `sudo groupdel hfc`

### Permisos
- **Cambiar usuario propietario de un archivo**: `sudo chown usuario archivo`
- **Cambiar grupo propietario de un archivo**: `sudo chgrp grupo archivo`
- **Cambiar usuario y grupo propietarios**: `sudo chown usuario:grupo archivo`

- **Cambiar permisos de forma numérica**: `sudo chmod 644 archivo`
- **Cambiar permisos de forma simbólica**: `sudo chmod u=rw,g+r,o-r archivo`
