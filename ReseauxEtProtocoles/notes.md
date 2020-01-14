# Notes

## Definition internet

C'est un réseau de réseaux, c'est récursif (réseaux dans un réseau). Il s'organise autour d'Autonomous Sytem (**AS**). Les AS dialoguent entre-elles en utilisant le Border Gateway Protocol (**BGP**). Chaque AS en interne utilise un protocole spécifique.
On retrouvera Open Shortest Path first **(OSPF)** , Routing Information Protocol (**RIP**), Intermediate System to Intermediate System (**IS-IS**).

L'Internet Ingeneering Task Force (**IETF**) est une organisation internationale regroupant des Request For Comments(**RFC**). Un RFC définit en détail un protocole pour internet.

## Autonomous Sytem (AS)

Il s'agit de domaines gérés par des organisations. Un domaine est une collection d'Internet Protocol (IP) connectés entre-eux sous un même préfixe de routing et controlé par les organisations susmentionnées. Chaque organisation a sa propre politique d'accès.

## IGP et EGP

(**IGP**) : *interior gateway protocol*.
C'est un protocole de routage intérieur à l'AS.

(**EGP**) : *exterior gateway protocol*
C'est un protocole de routage extérieur à l'AS.

## Border Gateway Protocol (BGP)

C'est le protocole standard utilisé pour échanger les routes et données d'accessibilité entre les différents AS. C'est un routage dynamique.

## Open Shortest Path first (OSPF)

Il s'agit d'un IGP se basant sur le protocole LSR. Il est le plus souvent utilisé dans les réseaux de grandes entreprises.

## Intermediate System to Intermediate System  (IS-IS)

Il s'agit d'un IGP se basant sur le protocole LSR lui aussi. Il est le plus souvent utilisé par les Fournisseurs D'Accès à Internet (**FAI**).

---

##  Open Systems Interconnection model (OSI model)

Décrit par:
<ul>
  <li>7 : APPLICATION</li>
  <li>6 : PRESENTATION</li>
  <li>5 : SESSION</li>
  <li>4 : TRANSPORT</li>
  <li>3 : RESEAUX</li>
  <li>2 : LIAISON DE DONNEES</li>
  <li>1 : PHYSIQUE</li>
</ul>

### 1 Physique

Au niveau matériel, se charge uniquement d'envoyer/recevoir un paquet. 

numérique → analogique
analogique → numérique

### 2 Liaison de données

On ajoute l'**adresse physique (MAC) du prochain routeur** à l'en-tête. Il utilise des protocoles de liaison notamment **Ethernet**. Il peut détecter une erreur au niveau physique et potentiellement la corriger.

Pour prévenir les collisions, il existe:

- CSMACD : **Collision Detection** son but est de détecter les collisions mais il n'est plus trop utilisé (WIFI)
- CSMACA : **Collision Avoidance** son but est d'éviter les collisions directement dans le protocole.

> On bourre le paquet si nécessaire ???

### 3 Réseaux

On ajoute **l'adresse IP du destinataire** finale en en-tête.

### 4 Transport

On segmente la donnée venant de la couche précédente à la bonne taille en plusieurs paquets si nécessaire.
On ajoute à l'en-tête le type de protocol utilisé en indicant le **port source** et le **port destination**. Chaque port correpondant à un protocole.

> Question: par exemple avec un serveur config en 8080, comment déterminer si c'est UDP/TCP

### 5 & 6 Session

Formatte les données

### 7 Réseaux

Offre une interface au processus pour communiquer par le réseau.

#### Media Access Control address (MAC)

C'est un identifiant unique associé à un Network Interface Controller (**NIC**).
Elle est composée de 6 groupes de 2 nombres hexadécimaux pouvant être séparés par

## TCP/IP

<div style="text-align:center"><img src="../administration_des_reseaux/assets/tcp_ip.png"/>
</div>

