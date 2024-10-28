# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](img/directorio.PNG)

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](img/volumen-host.PNG)
# COMPLETAR CON EL COMANDO

docker run -d --name contenedorp3 -p 80:80 -v D:/2024-B/CONSTRUCCION/practica3/nginx/html:/u
sr/share/nginx/html nginx:alpine

![image](https://github.com/user-attachments/assets/0b13a37a-257e-4297-9e57-a99aead5f49b)

### ¿Qué sucede al ingresar al servidor de nginx?

Si visitas http://localhost en tu navegador, verás el contenido de la carpeta html en el contenedor, que en este caso podría estar vacío o contener un archivo index.html inicial que hayas agregado.

### ¿Qué pasa con el archivo index.html del contenedor?

Al montar un volumen tipo host, el archivo index.html predeterminado del contenedor es reemplazado por el contenido de la carpeta html en el host. Si la carpeta html del host está vacía, el contenedor no mostrará nada en http://localhost.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?

Después de descargar y descomprimir la plantilla en la carpeta html, al ingresar al servidor de nginx nuevamente (http://localhost), verás la plantilla cargada y servida por el servidor nginx.

![image](https://github.com/user-attachments/assets/7afca6d1-04a8-40c3-96dd-ffe91753936a)

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO

docker rm -f contenedorp3

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?

Al volver a crear el contenedor, nginx cargará automáticamente los archivos existentes en la carpeta html del host, por lo que la plantilla de HTML5 UP aparecerá sin necesidad de copiar los archivos nuevamente.

### ¿Qué hace el comando pwd?

pwd imprime el directorio de trabajo actual en la terminal.

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

