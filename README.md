# Table des matières :
* Différents types de virtualisation :
    * Type I + Type II
    * o	Quel type de virtualisation utilisons-nous avec VMWare Workstation  ?

* RDP vs SSH :
    * Architecture client/serveur
    * SSh avec une IHM ?
    * Port ?
    * Protocole ?
    * (Schéma de l’infrastructure)

* Swap :
    * Concept (objectifs, limitations, sense dans un environnement virtualisé)
    * Dimensionner un swap ?
    * Comment tester un swap ?

* Type d’architecture :
    * Identifier les sources à obtenir pour installer Debian Duster

* Linus Torvals :
    * Son influence ?
    * Ou travaille-t-il actuellement ?
    * Git ?

# Les types de virtualisation 

* Type I :
    * Logiciel de virtualisation installé directement sur le matériel informatique.
    * Il est natif.
    * Un noyau hôte allégé et optimisé.
    * **Exemple :  Oracle VM, Microsoft Hyper-V.**

* Type II : 
    * s'exécute au sein de l'OS hôte, lui délégant ainsi la gestion du matériel sous-jacent.
    * Il est hébergé.
    * Un système d'exploitation invité s'exécutera donc en troisième niveau au-dessus du matériel. Les systèmes d'exploitation invités n'ayant pas conscience d'être virtualisés, ils n'ont pas besoin d'être adaptés.
    * **Exemple : VirtualBox d'Oracle, VMware Workstation, VMware Fusion**

![img 1 différences entre type I et II](https://github.com/besSejrani/MA-07/blob/main/imgs/Capture.PNG?raw=true)

# RDP vs SSH :

**Architecture client / serveur :** architecture logicielle dans laquelle les programmes d'application, dits clients, font appel, dans le cadre d'un réseau, à des services génériques distants fournis par des ordinateurs appelés serveurs.

**RDP & SSH :**
Ces outils vous permettent d'accéder et de gérer à distance d'autres ordinateurs, de transférer des fichiers et de faire pratiquement tout ce que vous pouvez faire en étant physiquement assis devant la machine :

* **Secure Shell (SSH)** pour les machines Linux, interface textuelle.
* **Protocole RDP (Remote Desktop Protocol)** pour les machines Windows, interface graphique.

**IHM (Interface Homme Machine) :** Les IHM permettent principalement d’afficher des informations de façon visuelle pour permettre à l’utilisateur de superviser un processus industriel.

**SSH & IHM ?**

**Oui !**
Il est possible d’utiliser le protocole SSH avec une interface graphique si l’on autorise le X11 Forwarding sur le serveur.

**Port & Protocole ?**

| Protocole        | Port           | Description  |
| :------------- |:-------------:| :-----|
| telnet     | 23 | Protocole utilisé sur tout réseau TCP/IP, permettant de communiquer avec un serveur distant en échangeant des lignes de texte |
| FTP      | 21      |  Protocole de communication destiné au partage de fichiers sur un réseau TCP/IP. |
| SSH | 22      |   Protocole conçu pour remplacer Telnet et FTP. |

> Le port SSH par défaut est le 22. (Pourquoi ? Car à l'époque où Tatu Ylonen a conçu le SSH pour remplacer à la fois telnet(port 23) et ftp(port 21), le port 22 était gratuit … ).

Protocole IPsec, défini par l'IETF comme un cadre de standards ouverts pour assurer des communications privées et protégées sur des réseaux IP, par l'utilisation des services de sécurité cryptographiques, est un ensemble de protocoles utilisant des algorithmes permettant le transport de données sécurisées sur un réseau IP.

* *IETF : (Internet Engineering Task Force) élabore et promeut des standards Internet, en particulier les standards qui composent la suite de protocoles Internet. L'IETF produit la plupart des nouveaux standards d'Internet.*

**Schéma :**
![Protocole SSH](https://github.com/besSejrani/MA-07/blob/main/imgs/Capture4.png?raw=true)
# Le Swap 
Le Swap est un espace sur un disque qui est utilisé lorsque la quantité de mémoire RAM physique est pleine. Lorsqu'un système Linux manque de RAM, les pages inactives sont déplacées de la RAM vers l'espace de swap.

L'espace de swap peut prendre la forme d'une partition de swap dédiée ou d'un fichier d'échange.
**MAIS ATTENTION :** l'utilisation de l'espace d'échange ralentit significativement le système et entraîne une activité permanente du disque dur, provoquant une usure prématurée du matériel. De ce fait, l'espace d'échange ne doit pas être considéré comme un remplacement de votre mémoire vive physique, mais plutôt comme un mécanisme d'appoint.

Dans la plupart des cas, lors de l'exécution de Linux sur une machine virtuelle, une partition de swap n'est pas présente, donc la seule option est de créer un fichier de swap.

**Dimensionner un swap ?**
Il n'y a pas qu'une seule règle définissant la quantité d'espace à allouer à la zone d'échange. Cependant, *on peut relever des recommandations généralement acceptées :*
* Votre ordinateur dispose de 6 Go de RAM ou plus.
Allouez un espace d'échange égal à la taille de votre RAM ;
* Votre ordinateur dispose de 1 Go de RAM à 4Go 
Allouez un espace d'échange de 1× à 1,5× la taille de votre RAM ;
* Votre ordinateur dispose de moins de 1 Go de RAM
Allouez un espace d'échange de 1,5× à 2× la taille de votre RAM.

**Comment tester un swap ?**

![img 2 vérifier l'état du swap](https://github.com/besSejrani/MA-07/blob/main/imgs/Capture2.png?raw=true)

# Type d’architecture :

Identifier les sources à obtenir pour installer Debian Duster :

[Versions Debian (download)](https://www.debian.org/releases/buster/debian-installer/)

![version debian](https://github.com/besSejrani/MA-07/blob/main/imgs/Capture3.png?raw=true)

# Linus Torvals :

>Il est connu pour avoir créé en 1991 (à 21 ans) le noyau Linux dont il continue de diriger le développement. Il en est considéré comme le « dictateur bienveillant à vie » (Benevolent Dictator for Life).

>Il a également créé le logiciel de gestion de versions décentralisée Git.

**Son influence ?**


[Why doesn't Linus Torvalds use Ubuntu or Debian ?](https://www.youtube.com/watch?v=qHGTs1NSB1s)

>Mais au début du développement, il monopolisait la partie de USENET dédiée à Minix, ce qui irrita son concepteur Andrew S. Tanenbaum, d'autant qu'il trouvait le noyau Linux techniquement obsolète. En effet, ce professeur de l'université d'Amsterdam était spécialisé dans la conception de systèmes d'exploitation. Minix était prévu pour permettre à un étudiant de comprendre rapidement son fonctionnement, et pour Tanenbaum, les noyaux des systèmes d'exploitation devaient être du type micro-noyau, à l'opposé du noyau dit monolithique autour duquel fut développé Linux à l'origine. Ce débat technique a donné lieu à de nombreuses réponses houleuses des deux créateurs et est resté célèbre.”

**Ou travaille-t-il actuellement ?**

Linux Foundation

**Git ?**

Git ne repose pas sur un serveur centralisé, mais il utilise un système de connexion “pair to pair”. 
Le code informatique développé est stocké non seulement sur l’ordinateur de chaque contributeur du projet, mais il peut également l'être sur un serveur dédié. 
C'est un outil de bas niveau, qui se veut simple et performant, dont la principale tâche est de gérer l'évolution du contenu d'une arborescence.

# Sources:

*Virtualisation*
* [Les types I et II](https://fr.wikipedia.org/wiki/Hyperviseur)

*RDP & SSH*
* [Architecture client/ serveur](https://www.larousse.fr/dictionnaires/francais/client-serveur/16523#:~:text=Architecture%20client%2Dserveur%2C,par%20des%20ordinateurs%20appel%C3%A9s%20serveurs.)

* [Actier SSH](https://phoenixnap.com/kb/ssh-to-connect-to-remote-server-linux-or-windows)

*SSH & IHM*
* [SSH](https://www.it-connect.fr/chapitres/a-quoi-sert-ssh/)


*Ports & Protocole* :
* [Port SSH](https://www.ssh.com/ssh/port)
* [IPsec](https://fr.wikipedia.org/wiki/IPsec)

* [Shémas SSH](http://sdz.tdct.org/sdz/mise-en-place-d-un-tunnel-tcp-ip-via-ssh.html)

*SWAP*
* [definition](https://doc.ubuntu-fr.org/swap)
* [taille](https://linuxize.com/post/create-a-linux-swap-file/)

*Linus Torvals*

* [Linus Torvald](https://fr.wikipedia.org/wiki/Linus_Torvalds)
