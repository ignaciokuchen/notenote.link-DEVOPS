# Como crear un VPN con Docker-Compose
Vamos a generar un server generico de Open VPN. 
</br>

## Archivo docker-compose.yaml
```
version: '2'
services:
  openvpn:
    cap_add:
     - NET_ADMIN
    image: kylemanna/openvpn
    container_name: openvpn
    ports:
     - "1194:1194/udp"
    restart: always
    volumes:
     - ./openvpn-data/conf:/etc/openvpn
     
```
</br>

##  Inicializamos los archivos de configuracion y certificados
Recorda susutituir la ip del servidor que va a contener la VPN.
```
docker-compose run --rm openvpn ovpn_genconfig -u udp://<IP-DE-TU-SERVIDOR> 
```
```
docker-compose run --rm openvpn ovpn_initpki
```
</br>

## Arregla tus permisos (puede no ser necesario si ya estás haciendo todo con root)

```
sudo chown -R $(whoami): ./openvpn-data
```
</br>

## Inicia el contenedor de OpenVPN
```
docker-compose up -d
```
</br>

## Puedes ver los logs de contenedor con:
```
docker-compose logs -f
```
</br>

## Generacion certificado de cliente
El nombre del cliente es el usuario que se utilizara para acceder, es recomendado no usar espacios
```
export CLIENTNAME="el_nombre_del_cliente"
# con contraseña
docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME
# sin contraseña
docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME nopass
```
## Crea el archivo de configuración del cliente
una vez generado el certificado, generamos la configuracion de la VPN, para que este se conecte. 
```
docker-compose run --rm openvpn ovpn_getclient $CLIENTNAME > $CLIENTNAME.ovpn
```
</br>

## Revoca el certificado de un cliente
```
# Dejando los archivos crt, key y req.
docker-compose run --rm openvpn ovpn_revokeclient $CLIENTNAME
# Borrando los correspondientes archivos crt, key y req.
docker-compose run --rm openvpn ovpn_revokeclient $CLIENTNAME remove
```