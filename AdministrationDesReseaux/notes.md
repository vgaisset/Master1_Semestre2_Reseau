# Administration des réseaux

## Rôle de l'administrateur

**Mettre en place**, **gérer** et **surveiller** le réseau.
Il est **responsable** de *TOUT* ce qui se passe sur ce réseau ou passe par ce réseau.

## Headers des diffèrentes couches

### Couche **transport** (TCP / UDP / ICMP / ARP / ...)

* Port de destination
* Port source

### Couche **réseau** (OSI) ou **accès** (TCP/IP) (IP)

* IP de destination
* IP source
* [TTL](#Time-To-Leave-(TTL))

### Couche **liaison de données** (OSI) ou **accès** (TCP/IP) (IP)

* Adresse MAC de destination
* Adresse MAC source
* [CS](#Checksum-(CS))

> On a pas parlé de **CS** en cours d'admin réseau, demander vérification.

## Time To Live (TTL, hop limit)

Compteur ou timestamp utilisé pour éviter de surcharger le réseau avec des paquets perdus ou mettant trop de temps à arriver. Le champs TTL est vérifié à chaque "saut", c'est à dire au passage de chaque routeur. Dans le cas d'un compteur, il est décrémenté, et s'il est égal à 0, le paquet **peut** être détruit.

## Checksum (CS)

Le checksum permet de vérifier l'intégrité d'une trame. 

> A compléter : il semble exister plusieurs manière de le calculer, ça serait bien de les noter là.

> Demander si CSMACA / CSMACD se basent sur le checksum.