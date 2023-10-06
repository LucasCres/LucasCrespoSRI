# CONFIGURACION DE UN SERVIDOR DHCP EN DEBIAN
### En este documento en markdown se va ha explicar como crear un servidor DHCP en debian y añadir un cliente windows10.
**Índice**   
1. [Configuracion de las maquinas](#id1)
2. [Configuracion de red de las maquinas](#id2)
3. [Configuracion del servidor DHCP](#id3)
4. [Cuarto apartado](#id4)
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







