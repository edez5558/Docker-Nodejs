# Docker-Nodejs
Gomez Alvarez Edmundo
## Introduccion

Docker es una plataforma de software que permite a los desarrolladores construir, empaquetar y desplegar aplicaciones en contenedores. Un contenedor es una unidad de software ligera y autónoma que incluye todo lo necesario para ejecutar una aplicación, incluyendo el código, las bibliotecas, las dependencias y las configuraciones del sistema.

La utilización de contenedores como los proporcionados por Docker, ofrece una serie de beneficios a los desarrolladores, ya que les permite trabajar de manera más eficiente y efectiva en varios aspectos. En primer lugar, los contenedores son portátiles, lo que significa que pueden ser ejecutados en cualquier plataforma que tenga Docker instalado, independientemente del sistema operativo o la infraestructura subyacente. Además, los contenedores son escalables, lo que permite a los desarrolladores crear y gestionar aplicaciones que pueden manejar una gran cantidad de tráfico y aumentar o disminuir la capacidad de manera eficiente y rápida.

Otro beneficio importante es que los contenedores son aislados, lo que significa que cada contenedor se ejecuta de forma independiente, y no afecta a otros contenedores o al sistema operativo subyacente. Esto hace que sea más fácil para los desarrolladores probar, depurar y actualizar sus aplicaciones sin preocuparse por conflictos con otros componentes del sistema.

## Desarrollo

Se utilizó la imagen oficial de Node.js que se encuentra disponible en Docker Hub (https://hub.docker.com/_/node). Esta imagen incluye una versión oficial de Node.js junto con algunos paquetes adicionales, y se puede utilizar como base para crear contenedores personalizados de Node.js.

Además, se siguió el tutorial oficial de Node.js sobre cómo utilizar Docker para desplegar una aplicación web (https://nodejs.org/ar/docs/guides/nodejs-docker-webapp).

```
FROM node:19-alpine

WORkDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 4000

CMD ["npm","start"]
```

```
docker build -t node-chat-app .
```

Para crear una imagen personalizada de Docker para la aplicación de Node.js, se debe crear un archivo de configuración llamado "Dockerfile" que describa los pasos necesarios para construir la imagen. Una vez que se ha creado el archivo "Dockerfile", se puede utilizar el comando "docker build" para construir la imagen.

```
docker images
```
![images](https://user-images.githubusercontent.com/122659695/226525636-feebb3c0-d2dc-44c0-b21c-4de76bd5c157.png)

Para verificar que la imagen se ha creado correctamente utilizamos "docker images", y nuestra imagen creada debe de aparecer.

Para ejecutar el contenedor y desplegar nuestra aplicación de Node.js, podemos utilizar el comando "docker run".

```
docker run -p 3000:4000 -d node-chat-app
```

![run](https://user-images.githubusercontent.com/122659695/226525237-41025222-6390-432e-9be6-17e50e5d266d.png)


El parámetro "-p" permite direccionar un puerto público en la máquina anfitriona a un puerto privado dentro del contenedor de Docker.

En el caso de la aplicación de Node.js, ésta está configurada para escuchar en el puerto 4000 dentro del contenedor de Docker. Sin embargo, para que la aplicación sea accesible desde fuera del contenedor, es necesario mapear el puerto privado 4000 al puerto público que se desee en la máquina anfitriona.

Y el parámetro "-d" permite ejecutar el contenedor en segundo plano (modo daemon).

```
docker ps
```

![ps](https://user-images.githubusercontent.com/122659695/226525267-2672b964-513a-4f5c-8363-b2153a3760cc.png)

Ya se podrá acceder a la aplicación desplegada en la dirección http://localhost:3000 desde un navegador web.

En la dirección mencionada se podrá ver la aplicación en funcionamiento, pudiendo interactuar con ella y comprobar que todo funciona correctamente. Este es uno de los principales beneficios de utilizar Docker para desplegar aplicaciones, ya que permite tener un entorno de ejecución aislado y portátil para la aplicación, lo que facilita su distribución y despliegue en diferentes entornos.


![node1](https://user-images.githubusercontent.com/122659695/226525525-cd0bbe00-df04-47ca-8612-124713504056.png)
![node2](https://user-images.githubusercontent.com/122659695/226525527-9b77bbcd-8c64-41d3-b5f9-6b01ea0193a6.png)

