# Serveur OpenSSH

## Installation OpenSSH

Openssh est constitué d'une architecture client/serveur, par conséquent, pour pouvoir se connecter sur le serveur à l'aide du protocole SSH, il faut installer préalablement un serveur SSH.

```text
sudo apt update
sudo apt install openssh-server
```

## Activation du service

Openssh-server tourne comme service de fond sous le nom de sshd, afin de le garantir à chaque redémarrage, il faut préalablement activer le service.

```text
sudo systemctl status sshd
sudo systemctl enable ssh
```



## Sources

| Titre | Lien |
| :--- | :--- |
| How To Install and Enable SSH Server on Debian 10 | [devconntected.com](https://devconnected.com/how-to-install-and-enable-ssh-server-on-debian-10/) |



