# Imagen
Es un archivo único que contiene todos los programas, librerías, dependencias y configuraciones necesarias para instalar y/o ejecutar una aplicación o un conjunto de aplicaciones.
![Imagen](img/imagen.PNG)


## ¿Cuál es la relación entre una imagen y un contenedor? 

En Docker una imagen se utliza para crear contenedores. 
### Imagen 
Es un archivo unico que contiene todos los programas, librerias, dependecias y configuraciones necesarias para instalar o ejecutar una aplicacion para funcionar correctamente.

### Contenedor
Es una instancia que se crea  a partir de una imagen. Los contenedores permiten ejecutar aplicaciones en entornos aislados, asegurando que funcionen de manera consistente sin importar en que sistema se desplieguen. 


![Imagen y contenedores](img/imagenContenedores.JPG)
## Comandos para imágenes

### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**
```
docker pull hello-world
```

![Imagen](img/docker_pull_hello_world.png)


![Imagen](img/docker_hello.png)

**¿Qué es nginx**

Nginx es un servidor web y proxy inverso de alto rendimiento. Es conocido por su capacidad para manejar múltiples conexiones simultáneas con un uso eficiente de recursos, y es ampliamente utilizado en servidores web para balanceo de carga, caching y como proxy inverso.

Descargar la imagen  **nginx** en la versión **alpine**
```
docker pull nginx:alpine
```

![Imagen](img/docker_nginx.png)


### Listar imágenes

```
docker images
```

![Imagen](img/ListarImagenes.png)


**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 

```
docker inspect hello-world
```

![Imagen](img/inspeccionar1.png)

![Imagen](img/inspeccionar2.png)


**¿Con qué algoritmo se está generando el ID de la imagen**
El ID de la imagen es generado usando el algoritmo de hash SHA-256.

### Filtrar imágenes

Si tenemos muchas imagenes descargadas y quieren buscar una especifica, usamos este comando:


```
docker images | grep <termino a buscar>
```

Por ejemplo, si quieren buscar la imagen nginx, utilizamos este comando:
```
docker images | grep nginx
```

![Imagen](img/Filtrar.png)


### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 

```
docker rmi hello-world
```

![Imagen](img/Eliminar1.png)


-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```

