# VLSM
Découverte des masques à longueurs variables

### Qu'est-ce que le VLSM?
```
VLSM, pour Variable Length Subnet Mask (soit masque de sous-réseaux à longueur variable) est une technique
utilisée dans le but de mieux gérer les adresses IP, tout comme le CIDR. En fait, VLSM est une extension
de CIDR. La différence est que le CIDR est plus utilisé au niveau internet et le VLSM est plus utilisé dans
un réseau local, mais les deux permettent de minimiser la perte d’adresses.
```

*Note: Pour mettre en place un réseau aux masques à longueurs variables, il faut être sûr que les routeurs supportent les protocoles compatibles au VLSM.Quelques-uns de ces protocoles sont OSPF, EIGRP, RIPv2, IS-IS*

https://www.inetdoc.net/articles/adressage.ipv4/adressage.ipv4.exercises.html

## Fonctionnement
![vlsm](https://user-images.githubusercontent.com/83721477/167432812-e9ba60fc-5e8e-44ba-a5ea-f9d36cdd5229.png)

### Calcule du 1er sous-réseau
1. On choisis le sous-réseau avec le plus d'hôtes (ici User)
2. On cherche un `2^x` supérieur à 100 (ici 2^7)<br> `2^7 = 128 - 2(réseau et broadcast) = 126 adresses ip`
3. On soustrait à 32 bits les 7 bits pour trouver la notation CIDR (le nouveau masque)<br> `32-7 = /25`
4. On a donc `192.168.0.0/25`<br> On effectue la méthode du `nombre magique` pour trouver la plage d'adresse<br>On aura `192.168.0.127` en dernière adresse.

### Calcule du 2ème sous-réseau
1. On choisis le 2ème sous-réseau avec le plus d'hôtes (ici Compta)
2. On cherche un `2^x` supérieur à 50 (ici 2^6)<br> `2^6 = 64 - 2(réseau et broadcast) = 62 adresses ip`
3. On soustrait à 32 bits les 6 bits pour trouver la notation CIDR (le nouveau masque)<br> `32-6 = /26`
4. On oublie pas de prendre la prochaine adresse après le 1er sous réseau (ici 192.168.0.128)
5. On a donc `192.168.0.128/26`<br> On effectue la méthode du `nombre magique` pour trouver la plage d'adresse<br>On aura `192.168.0.191` en dernière adresse.

### Calcule du 3ème sous-réseau
1. On choisis le 3ème sous-réseau avec le plus d'hôtes (ici Finance)
2. On cherche un `2^x` supérieur à 16 (ici 2^5)<br> `2^5 = 32 - 2(réseau et broadcast) = 30 adresses ip`
3. On soustrait à 32 bits les 5 bits pour trouver la notation CIDR (le nouveau masque)<br> `32-5 = /27`
4. On oublie pas de prendre la prochaine adresse après le 2ème sous réseau (ici 192.168.0.192)
5. On a donc `192.168.0.192/27`<br> On effectue la méthode du `nombre magique` pour trouver la plage d'adresse<br>On aura `192.168.0.223` en dernière adresse.

### Calcule du 4ème sous-réseau
1. On choisis le 4ème sous-réseau avec le plus d'hôtes (ici IT)
2. On cherche un `2^x` supérieur à 12 (ici 2^4)<br> `2^4 = 16 - 2(réseau et broadcast) = 14 adresses ip`
3. On soustrait à 32 bits les 4 bits pour trouver la notation CIDR (le nouveau masque)<br> `32-4 = /28`
4. On oublie pas de prendre la prochaine adresse après le 3ème sous réseau (ici 192.168.0.224)
5. On a donc `192.168.0.224/28`<br> On effectue la méthode du `nombre magique` pour trouver la plage d'adresse<br>On aura `192.168.0.239` en dernière adresse.

![vlsm](https://user-images.githubusercontent.com/83721477/167438577-572eaae7-e7f9-4dbb-9a66-dc7bf006deaf.png)
