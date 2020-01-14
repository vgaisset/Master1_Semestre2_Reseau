# Notes

## Definition internet

C'est un réseau de réseaux, c'est récursif (réseaux dans un réseau). Il s'organise autour d'[Autonomous Sytem](#Autonomous-System-(AS)) (**AS**). Les AS dialoguent entre-eux en utilisant le [Border Gateway Protocol](#Border-Gateway-Protocol-(BGP)) (**BGP**). Chaque AS en interne utilise un protocol spécifique. On retrouvera [Open Shortest Path First](#Open-Shortest-Path-First-(OSPF)) **(OSPF)** , Routing Information Protocol (**RIP**), [Intermediate System to Intermediate System](#Intermediate-System-to-Intermediate-System-(IS-IS)) (**IS-IS**).

L'Internet Ingeneering Task Force (**IETF**) est une organisation internationale regroupant des Request For Comments (**RFC**). Un RFC définit en détail un protocole pour internet.

## Autonomous System **(AS)**

Il s'agit de domaines gérés par des organisations. Un domaine est une collection d'Internet Protocol (IP) connectés entre-eux sous un même préfixe de routing et controlé par ces dîtes organisations. Chaque organisation a sa propre politique d'accès.

## **IGP** et **EGP**

(**IGP**) : *interior gateway protocol*.
C'est un protocole de routage intérieur à l'AS.

(**EGP**) : *exterior gateway protocol*
C'est un protocole de routage extérieur à l'AS.

## Border Gateway Protocol **(BGP)**

C'est le protocole standard utilisé pour échanger les routes et données d'accessibilité entre les différents AS. C'est un routage dynamique.

> Revoir ce que l'on entend par dynamique dans ce cas

## Open Shortest Path First **(OSPF)**

Il s'agit d'un [IGP](#IGP-et-EGP) se basant sur LSR protocol. Il est le plus souvent utilisé dans les réseaux de grandes entreprises.

## Intermediate System to Intermediate System  **(IS-IS)**

Il s'agit d'un [IGP](#IGP-et-EGP) se basant sur LSR protocol lui aussi. Il est le plus souvent utilisé par les Fournisseurs D'Accès à Internet (**FAI**).

---

##  Open Systems Interconnection model (OSI model)

Décrit par:

* 7: [APPLICATION](#Application-7)
* 6: [PRESENTATION](#Session-5-et-6)
* 5: [SESSION](#Session-5-et-6)
* 4: [TRANSPORT](#Transport-4)
* 3: [RESEAU](#Réseau-3)
* 2: [LIAISON DE DONNEES](#Liaison-de-données-2)
* 1: [PHYSIQUE](#Physique-1)

<ul>
  <li>7 : APPLICATION</li>
  <li>6 : PRESENTATION</li>
  <li>5 : SESSION</li>
  <li>4 : TRANSPORT</li>
  <li>3 : RESEAUX</li>
  <li>2 : LIAISON DE DONNEES</li>
  <li>1 : PHYSIQUE</li>
</ul>

> Dans ce modèle par couche, chaque couche utilise le service proposé par la couche inférieure, et donc fournit un service à la couche supérieure. Valable aussi pour [TCP/IP](#TCP/IP).

### Physique 1

Au niveau matériel, se charge uniquement d'envoyer/recevoir un paquet. 
numérique → analogique
analogique → numérique

### Liaison de données 2

On ajoute l'**adresse physique (MAC) du prochain routeur** et l'**adresse physique (MAC) de l'emetteur** à l'en tête. Il utilise des protocoles de liaison notament **Ethernet**. Il peut détecter une erreur au niveau physique et potentiellement la corriger.

Pour prévenir, et potentiellement corriger, les collisions, il exite:

- CSMA**CD** : **Collision Detection** son but est de détecter les collisions mais il n'est plus trop utilisé (WIFI)
- CSMA**CA** : **Collision Avoidance** son but est d'éviter les collisions directement dans le protocole.

> On bourre le paquet si nécessaire ???

### Réseau 3

On ajoute l'**adresse IP du destinataire final** et l'**adresse IP de l'emetteur** à l'en-tête.

### Transport 4

On segmente la donnée venant de la couche précédente à la bonne taille en plusieurs paquets si nécessaire. On ajoute à l'en-tête le type de protocol utilisé en indicant le **port source** et le **port destination**. Chaque port correpondant à un protocole. Les ports 1 à 1024 sont d'ailleurs réservés (serveur web **80**, serveur de transfert de fichiers **21**, serveur SSH **22**, etc...).

> Question: par exemple avec un serveur config en 8080, comment déterminer si c'est UDP/TCP

### Session 5 et 6

Formate les données

### Application 7

Offre une interface **(sockets)** au processus pour communiquer par le réseau.

#### Media Access Control address (MAC)

C'est un identifiant unique associé à un network interface controller (**NIC**).

## TCP/IP

<div style="text-align:center"><img src="../administration_des_reseaux/assets/tcp_ip.png"/>
</div>

