# Utilisateurs

## Création  d'un utilisateur

```text
adduser mysql
```

## Suppression d'un utilisateur

```text
deluser mysql
```

## Renommer un utilisateur

```text
usermod -l nouveauNom ancienNom
```

## Définir le mot de passe utilisateur

```text
passwd 123456789
```

## Ajouter un utilisateur existant à un groupe

```text
sudo usermod -aG nomGroup utilisateur
```

## Ajouter un nouvel utilisateur à un groupe

```text
useradd -G groupe utilisateur
```

## Supprimer un utilisateur d'un groupe

```text
gpasswd -d utilisateur groupe
```

## Litser tous les utilisateurs

```text
getent passwd

cat /etc/passwd
```

