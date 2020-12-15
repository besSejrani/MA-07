# Pare-feu

Definition d'un [pare-feu](https://opensource.com/article/18/9/linux-iptables-firewalld) :
>Un pare-feu est un ensemble de règles. Lorsqu'un paquet de données entre ou sort d'un espace réseau protégé, son contenu (en particulier les informations sur son origine, sa cible et le protocole qi'il envisage d'uitliser) est testé par rapport aux règles de pare-feu pour voir s'il doit être autorisé à passer.

![exemple](https://opensource.com/sites/default/files/uploads/iptables1.jpg) 

## Choix de l'outils :

Aucun parefeu n'est installer de base sur votre machine. Il s'agit à vous de choisir entre différents services de parefeu, comme par exemple aussi [iptable](https://en.wikipedia.org/wiki/Iptables) ou [firewalld](https://firewalld.org/).

Mais pour sa facilité de mise en fonction, nous avons opté d'utiliser l'outil [nftables](https://Wiki.debian.org/nftables).

- Il faudra avant l'installer
- Activer ses services

>aptitude installer nftables

>systemctl enable nftables.service

## INBOUND - Seul le port 22 est autorisé

Ma source principal et wiki de référence : [nftable.org](https://wiki.nftables.org/wiki-nftables/index.php/Quick_reference-nftables_in_10_minutes)

- Créer table interface réseau :

>sudo nft add table inet firewall

- Créer les règles :

>sudo nft 'add chain inet firewall input { type filter hook input priority 0; policy drop;}'

-------------------------------------------------------------------------------------------------

Source des : [droit](https://wiki.archlinux.org/index.php/nftables)

- "add rule inet firewall input" -> règle trafic

> sudo nft 'add rule inet firewall input tcp dport ssh accept comment "Accept SSH"'

- iif : 	Input interface index

> sudo nft 'add rule inet firewall input iif lo accept comment "Accept loopback traffic"'

- ct state : Connections

> sudo nft 'add rule inet firewall input ct state invalid drop comment "Drop invalid connections"'

> sudo nft 'add rule inet firewall input ct state established,related accept comment "Allow outbound traffic"'


## OUTBOUND - Aucune restriction

- Restriction Outpout :

>sudo nft 'add chain inet firewall output { type filter hook output priority 0; policy accept; }'

- Restriction Forward :

>sudo nft 'add chain inet firewall forward { type filter hook forward priority 0; policy drop; }'

Pour regarder ensuite si votre configuration est bonne :

> sudo nft list ruleset

* NOTE : La famille inet indique que la table sera traversée par les pacquets IPv4 et IPv6. Les règles propre à un type d’adresse n’impacteront pas l’autre type et vice-versa.



