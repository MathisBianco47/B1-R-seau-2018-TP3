<meta charset="UTF-8">

**Mathis BIANCO**

**Sacha Sallès**

# B1-Réseau-2018 TP3
-----------------

## Partie 1-4 Vue en cours
-----------------

### I.Création et utilisation simples d'une VM CentOS
*********************************************************
# 1.Création
  Création de ma VM effectue sur VirtualBox vue en cours.
-----------------
![alt text](CENTOS.png "githup")
![alt text](CENTOS3.png "TYPE NAT")

-----------------
# 2. Installation de l'OS
![alt text](CENTOS2.png "ensemble des caractérisations de ma VM")


# 3. Premier Boot
![alt text](CENTOS4.png "Désactivez SElinux")


# 4.Configuration réseau d'une machine CentOS
![alt text](CENTOS5.png "CONFIGterminale")

# 5.Faire joujou avec quelques commandes
![alt text](CENTOS6.png "PING")

<p>Pour le "curl"
Sur mon terminal j'ai indique "www.google.com"
Sur mon terminal j'ai indique "www.ynov.com

<p>Pour "dig"
j'ai du installer "sudo yum install bind-utils"
Ensuite dig www.google.com ou
dig www.ynov.com

L'IP est indique à la fin du terminal donc "192.31.80.30" (google)
L'IP est indique à la fin du terminal donc "192.55.83.30" (ynov)


# II. Notion de ports et SSH
**1. Exploration des ports locaux
-----------------
*Commande utilisez "SS" <br>
*commande utilisez pour vérifiez si ssh est bien installer. <br>
*effectuez sur un terminal de ma VM<br>
*"yum list installed openssh-server"
<br>
<br>
*other façon de vérifier SSH
*"ls -al /etc/ssh/sshd_config"
<br>
*voir l'état du du service SSH <br>
*"systemctl status sshd"

On indique cette commande pour seulement voir le port 22, il est bien "listen"
"ss -lntp |grep "22""
![alt text](CENTOS7.png "SSH")


### 2. SSH

![alt text](CENTOS8.png "PING")


### 3. Firewall
-----------------
**A.SSH**

`modifier le fichier`


![alt text](CentOS9.png "PING")

-----------------

![alt text](CentOS10.png "PING")





### III. Routage statique
-----------------
**Pour rappel, il faut désactiver SELinux.**
```
+ Le routage, c'est le fait d'utiliser une machine comme pivot (le routeur), entre deux réseau, afin qu'il fasse passer le trafic d'un réseau à un autre.
+ Le routage statique consiste à définir de façon simple les routes utilisables par le routeur et les machines.  
+ C'est  l'administrateur qui les définit à la main.
```
+ sudo setenforce 0
+ modifier le fichier /etc/selinux/config
+ modifier la valeur de SELINUX à permissive
+ SELINUX=permissive
+ pour vérifier : sestatus doit afficher Current mode: permissive


-----------------
**0. Rappels et objectifs**
```
+ deux PCs reliés avec un câble
+ les interfaces Ethernet des deux PCs étaient dans le même réseau pour pouvoir communiquer
+ "être dans le même réseau" c'est avoir une adresse IP dans le même réseau IP
```

![alt text](Centos11.png "PING")

-----------------

![alt text](Centos12.png "PING")

### 1. Préparation des hôtes (vos PCs)
-----------------

`Préparation avec câble`

+ Faites en sorte que :

+ vos deux PCs puissent se ping à travers le câble
+ vos carte Ethernet doivent être dans le réseau 12 : 192.168.112.0/30

**Préparation avec câble**


![alt text](Centos13.png "PING")


-----------------

**Préparation VirtualBox**


![alt text](Centos14.png "PING")

j'ai modifiez mon adresse avec : `192.168.102.10`
reussi !!

**Check**
-----------------
Nous avons été sur VB dans file, Host Network Manager, puis avons configuré nos IP des réseaux Host Only.
J'ai pris l'ip suivante `192.168.101.1`sur le réseau `192.168.101.0/24`.

Modification de l'adresse IP sur la VM avec Nano.


`reussi`

![alt text](Centos15.png "PING")


Observez vos tables de routage sur tous les hôtes, pour comprendre :

![alt text](Centos16.png "PING")

-----------------

**Activation du routage sur les PCs**

`MacOS`

-----------------
commande:  `sudo sysctl -w net.inet.ip.forwarding=1`

**2. Configuration du routage**


![alt text](Centos17.png "PING")

**Configuration du routage**

BILAN

| Appareil      |  IP(s)      |
| ------------- |-------------|
|PC1  ----------|192.168.112.22|
|VM1 -----------|192.168.101.10|
|PC2 -----------|192.168.112.23|
|VM2 -----------|192.168.102.10| 


PC1 accède déjà aux réseaux 1 et 12, il faut juste lui dire comment accéder au réseau 2, donc j'ai tapé la commande
`route -n add -net 192.168.102.0/24 192.168.112.2`



-----------------

**PC2**

+ PC2 devrait pouvoir ping 192.168.101.1 (l'adresse de PC1 dans 1)


![alt text](Centos18.png "PING")

-----------------


![alt text](Centos19.png "PING")

-----------------


![alt text](Centos20.png "PING")


**VM1**

![alt text](Centos20.png "PING")

## PING VM1 à VM2

Nous ne sommes pas parvenus à pinguer nos deux VM, une erreurs d'IP récalcitrante (on à pas réussi à redefinir l'IP sur le centOS, il nous crachait une erreur) nous à torturée l'esprit sur mon mac, nous y étions presque. 
Avec plus de temps nous l'aurions fait. Nous sommes sincèrement désolé.



