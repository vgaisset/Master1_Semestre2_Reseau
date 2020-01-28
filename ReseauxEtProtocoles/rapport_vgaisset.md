# rapport TD 1

## 2 - Commandes

### Question 1

|Interface|Adresse IP|Masque de sous-réseau|Passerelle par défaut|Taille maximale d'un paquet|
|--|--|--|--|--|
|eth0|10.0.203.5|255.255.255.0|10.0.203.254|9000 (jumbo ethernet)|
|lo|127.0.0.1|255.0.0.0||65536|

Commandes (ifconfig) :
 * /sbin/ifconfig
 * /usr/sbin/route

Commandes (ip) :
 * ip address
 * ip route

 L'interface **lo** est l'interface de *loopback*, qui est une interface virtuelle permettant notamment de tester sa configuration réseau. Elle permet aussi de s'envoyer des trames à soi-même.

 ### Question 2

* ifconfig :

**Eteindre l'interface** : /sbin/ifconfig eth0 **down**

**Allumer l'interface** : /sbin/ifconfig eth0 **up**

 * ip :

**Eteindre l'interface** : ip link set eth0 **down**

**Allumer l'interface** : ip link set eth0 **up**

Ces commandes ne peuvent pas être exécutées, elles nécessitent les droits d'administrateur.

### Question 3 :

Ping utilise **ICMP** (couche transport).

L'en-tête d'ICMP contient l'information que c'est un ping, et donc l'hôte "pingé" répond.

Le serveur du LABRI ne répond pas par configuration.

### Question 4

**Table ARP :**

Fait la correspondance adresse MAC <-> IP (seulement sur le réseau local).

|Adresse|MAC|Commentaire|
|--|--|--|
|riker.emi.u-bordeaux.fr | 54:bf:64:8f:4a:fe | voisin |
|data.emi.u-bordeaux.fr | 54:bf:64:8f:5a:74 | voisin |
|vlan203-routeur.emi.u-bordeaux.fr | 58:20:b1:b1:23:00 | passerelle |
|kirk.emi.u-bordeaux.fr | 54:bf:64:8f:55:14 | voisin |

Un paquet ARP contient soit une requête (qui a tel IP ?) soit une réponse (J'ai cette IP, voici mon adresse MAC).

Pour la requête, on demande à tout le monde (broadcast) en utilisant l'adresse MAC **FF:FF:...:FF**.

La table permet de ne pas refaire de requête ARP sur les hôtes du même sous-réseau connus.

### Question 5

**traceroute** fonctionne par ping successifs.

Il utilise le TTL (en le mettant à 1). Le premier routeur rencontré détruit le paquet et l'emetteur utilise la notification de destruction pour connaitre le routeur. Et ainsi de suite avec TTL = 2 pour connaitre le deuxième routeur, etc...

Cette commande permet donc de connaitre la route empruntée (routeurs traversés) par un paquet jusqu'à sa destination.

En sortant du réseau Renater, les traceroutes sont bloqués. Les routeurs peuvent détecter le traceroute en regardant un flag dans ICMP ou voir que le TTL est très faible.

### Question 6

On observe des informations sur le détenteur du bloc d'adresses (**88.0.0.0** -> **88.15.255.255**).

**88.12.47.5** appartient à **Telefonica de Espana**.
Cette plage appartient à l'AS 3352

L'option **-a** permet de récupérer les informations depuis des miroirs.

### Question 7

Résultat de la commande **traceroute www.google.com** depuis un pc personnel, sur un réseau privé :

|Hôte|détenteur|
|---|---|
|_gateway (192.168.0.1)|Internet Assigned Numbers Authority (adresse privée, passerelle)|
|10.45.0.1 (10.45.0.1)|Internet Assigned Numbers Authority (adresse privée)|
|lha1rj-ge-1-1-5.200.numericable.net (213.245.253.129)|SFR SA|
|ip-65.net-80-236-3.static.numericable.fr (80.236.3.65)|SFR SA|
|ip-161.net-80-236-1.static.numericable.fr (80.236.1.161)|SFR SA|
|* * \*|* * *|
|216.239.48.142 (216.239.48.142)|Google LLC|
|par10s38-in-f4.1e100.net (172.217.18.196)|Google LLC|


### Question 8

|Nom|Adresse|
|---|---|
|www.labri.fr|147.210.8.59|
|www.u-bordeaux.fr (alias : v-frtwww.01.u-bordeaux.fr)|147.210.215.26|
|b3a1.emi.u-bordeaux.fr|147.210.12.254|

### Question 9

Contrairement à la commande précédente, **dig** semble montrer les sous-domaines (et leurs adresses IPv4 et IPv6) liés au nom recherché.

Adresse du serveur de nom : 10.0.220.13

Pour utiliser un autre serveur DNS, on peut utiliser '**@**'.
Exemple : **dig www.labri.fr @8.8.8.8** pour utiliser le serveur DNS à l'adresse 8.8.8.8.

### Question 10

Les connexions actives sont les connexions avec l'état **ESTABLISHED**. Les connexions en attente sont les autres (état **TIME_WAIT**).

> Même après s'être connecté en SSH, la liste des connexions actives ne change pas..

L'option **-a** permet d'afficher les "serveurs". Cela semble être les sockets UDP et les sockets TCP qui écoutent.

### Question 11

|Commande Windows|Commande Linux|
|---|---|
|ipconfig|ifconfig|
|arp -a|arp -a|
|netstat|netstat|
|netstat -a|netstat -a|
|tracert \<host\>|traceroute \<host\>|
|hostname|hostname|
|ping|ping|
|nslookup  \<hostname>|host \<hostname>|
|route PRINT|route|

## 3 - Traces et encapsulation

### Question 1

L'adresse MAC est répétée car ARP (couche 3) n'a pas accès à l'adresse MAC contenue dans l'en-tête ethernet (couche 2).

L'adresse 00:00:00:00:00:00 est utilisée car on cherche justement cette adresse MAC.
On peut noter que la trame ethernet fait toujours au moins 64 octets. De ce fait, une trame ARP est toujours bourrée à la fin.

Ici, l'adresse MAC de destination n'est pas l'adresse de broadcast. Celà est dû au fait que Le protocole VRRP permet d'avoir plusieurs routeurs représentés par une seule adresse MAC et IP virtuelles.

### Question 2

|Nom|Valeur|
|---|---|
|MAC destination|00:26:22:2e:67:f0|
|MAC source|00:18:fe:85:25:80|
|Protocole de couche 3|08 00 (IP)|
|Protocole de couche 4|11 (UDP)|
|IP destination|93.d2.81.2c (147.210.129.44)|
|IP source|93.d2.08.7e (147.210.8.126)|
|Port source|00 35 (53)|
|Port destination|f0 68 (61544)|

D'après le port source (53), on peut supposer qu'il s'agit d'une réponse à une requête DNS. De plus, d'après la représentation ASCII, il semblerait que l'hôte pour lequel on recherche l'adresse soit google (www.google.com).