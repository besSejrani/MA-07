# Configuration Fichier SSHD

## Sécurité

Comprendre que la sécurité d'un système n'est pas un besoin, mais une nécessité, est primordial.  Ainsi, il serait judicieux de sécuriser l'accès SSH du serveur afin de contrôler l'accès de ce dernier.

Idéalement, on souhaiterait désactiver la connection au compte Root en SSH, désactiver l'authentification par mot de passe, activer l'authentification par clé privé/publique afin d'éviter les attaques en masse.

## Clé Publique & Privée

### Informations

En informatique, le meilleur moyen pour encrypter les informations durant un transfert données depuis un ordinateur à un autre se fait à l'aide d'une clé privée et d'une clé publique.

 Chaque ordinateur génère une paire et n'envoie à l'autre que la clé publique. La clé privée peut ensuite, à l'aide de la clé publique reçue, décrypter les informations.

Idéalement, la paire est généré depuis le client, puis la clé publique est ensuite envoyé au serveur. Il est recommandé de garder la clé privée en sécurité, probablement sur une clé USB.

### Générer une paire de clé privée & publique

Par défaut, la paire sera créé dans un dossier caché, nommé .ssh, dans le dossier de l'utilisateur.

```text
ssh-keygen -t rsa -b 4096
```

### Copier & envoyer la clé publique

```text
ssh-copy-id -i chemin/cle/publique utilisateur@ip
```

## Paramétrer le serveur Openssh

### Fichier de configuration

Le fichier de configuration se trouve par défaut au chemin suivant.

```text
cat /etc/ssh/sshd_config
nano /etc/ssh/sshd_config
```

Voici les options à modifier pour parvenir à ces modifications.

```text
PermitRootLogin: no
PubkeyAuthentication: yes 
AuthorizedKeysFile %h/.ssh/authorized_keys
PasswordAuthentication: no
```

