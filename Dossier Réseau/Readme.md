<meta charset="UTF-8">
<p> Mathis BIANCO B1A </p> 
<p> Sacha Sallès </p> 

**B1-Réseau-2018 TP3**
-----------------

#***Partie 1-4 Vue en cours*** 
<br>

***# I.Création et utilisation simples d'une VM CentOS***
*********************************************************
#1.Création
  Création de ma VM effectue sur VirtualBox vue en cours.
-----------------
![alt text](CENTOS.png "githup")
![alt text](CENTOS3.png "TYPE NAT")

-----------------
#2. Installation de l'OS
![alt text](CENTOS2.png "ensemble des caractérisations de ma VM")


#3. Premier Boot
![alt text](CENTOS4.png "Désactivez SElinux")


#4.Configuration réseau d'une machine CentOS
![alt text](CENTOS5.png "CONFIGterminale")

#5.Faire joujou avec quelques commandes
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


#II. Notion de ports et SSH

**#1. Exploration des ports locaux**
**************************************
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


#2. SSH
<br>
![alt text](CENTOS8.png "PING")


***#3. Firewall***
******************
nothing


### III. Routage statique
