DOCKER COMPOSE y NETWORK

1. **Configuración de una red en Docker:**
   Para crear la red, se utilizó el comando `docker network create --driver=bridge --subnet=172.29.0.0/16 --ip-range=172.29.5.0/24 --gateway=172.29.5.254 franconet`. El nombre asignado a la red es `franconet`.

2. **Desplegar dos contenedores en la nueva red:**
   El primer contenedor se lanza con `docker run -itd --name=francoUNO --network=franconet ubuntu`. Para el segundo contenedor, se ejecuta `docker run -itd --name=francoDOS --network=franconet ubuntu`. Ambos quedan conectados a la red `franconet` con sus nombres respectivos.

3. **Verificación de contenedores en la red:**
   Usa el comando `docker network inspect franconet` para observar la configuración y confirmar la conexión de los contenedores a la red.

4. **Comprobar comunicación entre los contenedores:**
   Para instalar la utilidad `ping`, ejecuta `apt install -y iputils-ping`. Después, desde `francoUNO` verifica la conexión hacia `francoDOS` usando `ping francoDOS`.

5. **Listado de contenedores conectados:**
   Muestra todos los contenedores activos en la red ejecutando `docker network ls`.

6. **Consultar detalles de la red:**
   Para obtener las propiedades de `franconet`, usa `docker network inspect franconet` y revisa la información de configuración de la red.

7. **Crear una red adicional:**
   Para establecer una nueva red con diferentes ajustes, usa el comando `docker network create --driver=bridge --subnet=172.33.0.0/16 --ip-range=172.30.5.0/24 --gateway=172.30.5.254 franconet2`.

8. **Iniciar dos contenedores en la segunda red:**
   Conecta dos contenedores a la red `franconet2` con `docker run -itd --name=francoA --network=franconet2 ubuntu` y `docker run -itd --name=francoB --network=franconet2 ubuntu`.

9. **Prueba de conexión entre los contenedores en redes separadas:**
   Realiza un ping desde `francoA` hacia `francoUNO`. Debería fallar al estar en redes diferentes. No obstante, desde `francoA` puedes hacer ping a `francoB` porque ambos están en `franconet2`.

### Docker Compose

10. **Guía de inicio en Docker Compose:**
    Primero, crea el archivo de configuración donde se definen los contenedores y servicios necesarios. Luego, al ejecutar `docker-compose up`, se despliega el entorno completo. Puedes acceder a `localhost` desde un navegador para confirmar que el servicio está en funcionamiento.

11. **Configuración en Docker Compose para tres contenedores en una red común:**
    En el archivo `.yaml`, define estos parámetros:
    - **version**: Define la versión de Docker Compose.
    - **volumes**: Monta un directorio en los contenedores.
    - **image**: Especifica la imagen Docker (ej., `httpd`).
    - **container_name**: Nombre de cada contenedor.
    - **networks**: Red de conexión de los contenedores.
    - **ports**: Mapea los puertos entre el contenedor y la máquina anfitriona.

12. **Explorar cuatro configuraciones adicionales en Docker Compose:**
    - **depends_on**: Establece el orden de inicio entre servicios.
    - **environment**: Define variables de entorno para los contenedores.
    - **restart**: Configura cuándo y cómo reiniciar los contenedores.
    - **labels**: Añade etiquetas personalizadas a los contenedores para su organización.
