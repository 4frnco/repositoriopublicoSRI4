# repositoriopublicoSRI4
DOCKER NETWORK Y COMPOSE

1. Crear una red en Docker:
Para crear la red, se utilizó el comando docker network create --driver=bridge --subnet=172.29.0.0/16 --ip-range=172.29.5.0/24 --gateway=172.29.5.254 franconet. El nombre de la red es franconet.

2. Crear dos contenedores conectados a la red:
Para el primer contenedor, se usó el comando docker run -itd --name=francoUNO --network=franconet ubuntu. Para el segundo contenedor, el comando fue docker run -itd --name=francoDOS --network=franconet ubuntu. Cada contenedor se conecta a la red franconet con el nombre asignado.

3.Comprobar que los contenedores están en la red:
Ejecuta el comando docker network inspect franconet para ver la configuración de la red y verificar los contenedores conectados.
