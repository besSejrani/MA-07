# Firewall

## Pare-feu

### Définition

> Un pare-feu est un ensemble de règles. Lorsqu'un paquet de données entre ou sort d'un espace réseau protégé, son contenu \(en particulier les informations sur son origine, sa cible et le protocole qi'il envisage d'utiliser\) est testé par rapport aux règles de pare-feu pour voir s'il doit être autorisé à passer.

[![exemple](https://camo.githubusercontent.com/9aa7c68aa9b3be66fa6708e486b84e2a5ea6f1a04d087317b8742abea58c11bc/68747470733a2f2f6f70656e736f757263652e636f6d2f73697465732f64656661756c742f66696c65732f75706c6f6164732f69707461626c6573312e6a7067)](https://camo.githubusercontent.com/9aa7c68aa9b3be66fa6708e486b84e2a5ea6f1a04d087317b8742abea58c11bc/68747470733a2f2f6f70656e736f757263652e636f6d2f73697465732f64656661756c742f66696c65732f75706c6f6164732f69707461626c6573312e6a7067)

### Outils

Aucun pare-feu n'est installer de base sur votre machine. Il s'agit à vous de choisir entre différents services de pare-feu, comme par exemple aussi [iptable](https://en.wikipedia.org/wiki/Iptables) ou [firewalld](https://firewalld.org/).

Mais pour sa facilité de mise en fonction, nous avons opté d'utiliser l'outil [nftables](https://wiki.debian.org/nftables).

```text
sudo apt install nftables

sudo systemctl enable nftables
```

## INBOUND

### Créer table interface réseau

```text
sudo nft add table inet firewall
```

### Création de règles 

```text
sudo nft 'add chain inet firewall input { type filter hook input priority 0; policy drop;}'
```

### Règles trafic

```text
sudo nft 'add rule inet firewall input tcp dport ssh accept comment "Accept SSH"'
```

### iif : Input interface index

```text
sudo nft 'add rule inet firewall input iif lo accept comment "Accept loopback traffic"'
```

### ct state : Connections

```text
sudo nft 'add rule inet firewall input ct state invalid drop comment "Drop invalid connections"'

sudo nft 'add rule inet firewall input ct state established,related accept comment "Allow outbound traffic"'
```

### OUTBOUND

### Restriction Outpout

```text
sudo nft 'add chain inet firewall output { type filter hook output priority 0; policy accept; }'
```

### Restriction Forward

```text
sudo nft 'add chain inet firewall forward { type filter hook forward priority 0; policy drop; }'
```

## Vérification

```text
sudo nft list ruleset
```

{% hint style="info" %}
La famille inet indique que la table sera traversée par les pacquets IPv4 et IPv6. Les règles propre à un type d’adresse n’impacteront pas l’autre type et vice-versa.
{% endhint %}

## Sources

| Titre | Lien |
| :--- | :--- |
| Définition Pare feu  | [pare-feu](%20https://opensource.com/article/18/9/linux-iptables-firewalld) |
| Nftables | [Nftables](https://wiki.nftables.org/wiki-nftables/index.php/Quick_reference-nftables_in_10_minutes) |
| Rules | [Rules](https://wiki.archlinux.org/index.php/nftables) |
| Diagramme | [Image](https://camo.githubusercontent.com/9aa7c68aa9b3be66fa6708e486b84e2a5ea6f1a04d087317b8742abea58c11bc/68747470733a2f2f6f70656e736f757263652e636f6d2f73697465732f64656661756c742f66696c65732f75706c6f6164732f69707461626c6573312e6a7067) |

