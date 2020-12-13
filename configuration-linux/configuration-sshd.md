# Configuration Fichier SSHD

## Sécurité

Comprendre que la sécurité d'un système n'est pas un besoin, mais une nécessité, est primordial.  Ainsi, il serait judicieux de sécuriser l'accès SSH du serveur afin de contrôler l'accès de ce dernier.

## Configuration

### Fichier de configuration

Le fichier de configuration se trouve par défaut au chemin suivant.

```text
cat /etc/ssh/sshd_config
```

Idéalement, on souhaiterait désactiver la connection au compte Root en SSH, désactiver l'authentification par mot de passe, activer l'authentification par clé privé/publique afin d'éviter les attaques en masse. Voici les options à modifier pour parvenir à ces modifications.

```text
PermitRootLogin: no
PubkeyAuthentication: yes 
AuthorizedKeysFile %h/.ssh/authorized_keys
PasswordAuthentication: no
```

