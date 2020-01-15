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

## Routeur

Utilise les 3 premières couches du modèles OSI. La trame remonte à la couche 3, à laquelle on regarde l'IP du destinataire final. A partir de là, on construit une nouvelle trame en mettant en adresse MAC de destination l'adresse MAC du prochain routeur ou du destinataire final, si celui-ci est connecté au routeur.

Quand la nouvelle trame est créée, elle est envoyée par la couche physique. La technologie utilisée peut varier, cela peut être de l'ethernet, du FTH (fibre optique), du HSPA (4G) etc...

Ce système de couche permet de traiter les paquets de manière identique, indépendamment de la technologie employée pour faire naviguer la trame sur le réseau.

> Demander si cette partie vaut aussi pour les switchs (notamment la couche physique).

## Adresse de transport

Adresse représentant l'émetteur d'une trame. Il s'agit du couple :

* IP source
* Port local

## Connexion

"Lien" entre deux applications. Elle est représentée par le 4-uplet :

* IP source
* Port source
* IP destination
* Port destination

> Il y avait une histoire d'implémentation de TCP qui, dans un soucis de performance, n'utilise pas ce tuple pour identifier la connexion. Si quelqu'un s'en souvient et peut compléter...

## TCP

### Header

| Ps | Pd | Syn | Fin | Ack | Psh | Urg | Rst | Numéro de séquence | Numéro d'aquitement |
|---|---|---|---|---|---|---|---|---|---|
|||||||||||
