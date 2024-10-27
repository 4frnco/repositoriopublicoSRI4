# repositoriopublicoSRI4
DOCKER NETWORK Y COMPOSE

1. **Crear una red en Docker:**
   Para crear la red, se utilizó el comando `docker network create --driver=bridge --subnet=172.29.0.0/16 --ip-range=172.29.5.0/24 --gateway=172.29.5.254 franconet`. El nombre de la red es `franconet`.

2. **Crear dos contenedores conectados a la red:**
   Para el primer contenedor, se usó el comando `docker run -itd --name=francoUNO --network=franconet ubuntu`. Para el segundo contenedor, el comando fue `docker run -itd --name=francoDOS --network=franconet ubuntu`. Cada contenedor se conecta a la red `franconet` con el nombre asignado.

3. **Comprobar que los contenedores están en la red:**
   Ejecuta el comando `docker network inspect franconet` para ver la configuración de la red y verificar los contenedores conectados.

4. **Comprobar conectividad entre los contenedores:**
   Instala la utilidad `ping` en los contenedores ejecutando `apt install -y iputils-ping`. Desde el primer contenedor, verifica la conexión con el segundo ejecutando `ping francoDOS`.

5. **Listar contenedores conectados a la red:**
   Para listar los contenedores en la red, usa `docker network ls`.

6. **Ver las propiedades de la red:**
   Ejecuta `docker network inspect franconet` para obtener detalles específicos sobre la configuración y propiedades de la red.

7. **Crear una segunda red:**
   Crea una nueva red similar a `franconet`, pero con un nombre y configuraciones de IP diferentes. Usa el comando `docker network create --driver=bridge --subnet=172.33.0.0/16 --ip-range=172.30.5.0/24 --gateway=172.30.5.254 franconet2`.

8. **Lanzar dos contenedores conectados a la nueva red:**
   Crea dos contenedores en la nueva red `franconet2` con los comandos `docker run -itd --name=francoA --network=franconet2 ubuntu` y `docker run -itd --name=francoB --network=franconet2 ubuntu`.

9. **Comprobar conexiones entre los cuatro contenedores:**
   Intenta hacer ping desde el contenedor `francoA` a `francoUNO`. Al pertenecer a redes distintas, el ping debería fallar. Sin embargo, desde `francoA` deberías poder hacer ping a `francoB`, ya que ambos están en la misma red.

Docker Compose

10. **Sigue los pasos de la guía de iniciación de Docker Compose y explica el procedimiento:**
    Primero, se crea el archivo de configuración en el cual se especifican los contenedores y servicios necesarios. Luego, al ejecutar `docker-compose up`, se despliega el entorno completo. Abriendo `localhost` en el navegador, se puede verificar que el servicio funciona y ver la actividad en la terminal.

11. **Crear un archivo de configuración para Docker Compose con tres contenedores en una red compartida:**
    En el archivo `.yaml`, define los siguientes parámetros:
    - **version**: La versión de Docker Compose.
    - **volumes**: Monta un directorio para los contenedores.
    - **image**: La imagen de Docker, por ejemplo `httpd`.
    - **container_name**: Nombre del contenedor.
    - **networks**: Red a la que se conectan los contenedores.
    - **ports**: Mapear los puertos entre los contenedores y la máquina local.

12. **Probar y explicar cuatro configuraciones adicionales en Docker Compose:**
    - **depends_on**: Define el orden en el cual deben iniciarse los servicios.
    - **environment**: Establece variables de entorno para los contenedores.
    - **restart**: Configura el comportamiento de reinicio de los contenedores.
    - **labels**: Agrega etiquetas a los contenedores para organizar y categorizar el entorno.

