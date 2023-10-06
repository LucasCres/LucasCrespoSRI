# CONFIGURACION DE UN SERVIDOR DHCP EN DEBIAN
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/5fda6fd3-5c01-4924-8fff-27f1d537bf86)

### En este documento en markdown se va ha explicar como crear un servidor DHCP en debian y añadir un cliente windows10.
**Índice**   
1. [Configuracion de las maquinas](#id1)
2. [Configuracion de red de las maquinas](#id2)
3. [Configuracion del servidor DHCP](#id3)
4. [Unir el cliente](#id4)
## Configuracion de las maquinas<a name="id1"></a>
### En primer lugar esta es la configuracion inicial del Pfsense tiene que tener una tarjeta en adaptador puente y otra en red interna en mi caso ASIR203.
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/1bf26fd0-0b1b-41eb-ab46-e6bac95b1ac7)
### Lo siguiente seria la configuracion inicial del Debian nuestro servidor DHCP que tiene una tarjeta de red en red interna la misma red que el pfsense obviamente.
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/31dc6d89-35ba-4a7c-9b7d-756f7e0e7319)
### Y por ultimo un cliente en mi caso Windows10 tambien en red interna 
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/658b4291-27e0-4201-95ba-dff96d5700c2)

## Configuracion de red de las maquinas<a name="id2"></a>
### Seguimos con la configuracion de las maquinas pero en este caso ya dentro de las maquinas en primer lugar el Pfsense donde no hay que hacer mucha cosa con cambiar la ip de la tarjeta con red interna por 192.168.x.1 en mi caso la 3 y desactivar el DHCP que trae por defecto estaria listo.
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/6733a966-a2d6-41ba-bdea-cc93c4261366)
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/31d9fe93-1f41-4a2f-bca6-4b1c353efc72)
### Proseguimos con el Debian en cuanto a configuracion de red tampoco tiene mucha cosa con asignarle una ip fija y poner bien el DNS estaria configurada la tarjeta de red la ip asignada sera la .50
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/05189d7b-0bfc-42e1-8fcf-af1975524adc)
### En el equipo cliente de momento no vamos a hacer nada hasta que no tengamos configurado el servidor DHCP

## Configuracion del servidor DHCP<a name="id3"></a>

### Como primer paso empezaremos instalando los servicios DHCP Debian al servidor usando el siguiente comando.
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/fbf89472-3838-4833-9b9c-b62028205a18)
### El servicio DHCP solo debe estar disponible para la red interna por eso debe aceptar conexiones por la interfaz interna para esto primero haremos un  `ip a` para saber nuestra tarjeta de red en mi caso la enp0s3
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/0ef911ca-fac1-4284-a047-e000faa45abf)

### Ya sabiendo esto deberemos editar el archivo /etc/default/isc-dhcp-server para ello haremos un nano a este y en el apartado ipv4 pondremos nuestra tarjeta de red.

![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/c10f5b3a-c687-4e61-a2ce-679c5166ba0b)

### Ahora vamos con la parte importante de la configuracion si se falla aqui lo mas probable es que no te funcione vamos a editar el archivo /etc/dhcp/dhcpd.conf hacemos un nano.
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/d3bccfdb-ec47-499a-bea1-3534138baa14)
### En la primera parte del documento no hay que tocar nada para que funcione se deja como esta.
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/1e870df3-fb1c-4984-a3a8-e53fa0011c90)
### Bajamos en el documento hasta llegar donde aparece algo como esto pero comentado le quitamos la almohadilla y editamos con nuestras ip al principio se puede ver la subnet y la mascara seguido el rango de direcciones y la ip de nuestro Pfsense en la linea siguiente hay que poner el DNS y luego el nombre de nuestro dominio en mi caso asir03.com y el lease time.
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/31e7aea3-d3e4-4282-a289-b5f3f7f48ff9)
### Una vez teniendo configurado ese fichero solo haria falta iniciar el servidor dhcp unir el cliente y comprobar que le ha asignado una ip comencemos iniciandolo usando el comando `sitemctl start isc-dhcp-server`
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/e0221443-d59d-4118-afec-735d11853300)
### Y para comprobar que ha ido bien usaremos `systemctl status isc-dhcp-server`
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/b2107d8e-dbce-418b-ab21-472914aa0737)
## Unir el cliente <a name="id4"></a>
### Una vez todo configurado es momento de unir el cliente windows10 con asegurarse de que esta en la misma red y por si acaso poner el mismo dns deberia unirse automaticamente con una ip asignada dentro del rango
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/0f619c26-de15-44de-965d-408f55a859f2)
### Hacemos un ipconfig para comprobarlo y si tiene la ip bien asignada estaria todo correcto y finalizado.
![image](https://github.com/LucasCres/LucasCrespoSRI/assets/144890487/6aeb26b8-a72d-4e65-a6a3-7dcc26ceb69d)








