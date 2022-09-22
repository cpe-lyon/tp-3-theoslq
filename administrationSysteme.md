**TP 3 Utilisateurs, groupes et permissions**

**Exercice 1**

1. 
```console
User@localhost:~$ groupadd dev
User@localhost:~$ groupadd infra
```
2. 
```console
User@localhost:~$ sudo useradd -m alice
User@localhost:~$ sudo useradd -m bob
User@localhost:~$ sudo useradd -m charlie
User@localhost:~$ sudo useradd -m dave
```
3.
```console
User@localhost:~$ sudo gpasswd -a alice dev
User@localhost:~$ sudo gpasswd -a bob dev
User@localhost:~$ sudo gpasswd -a dave dev
User@localhost:~$ sudo gpasswd -a bob infra
User@localhost:~$ sudo gpasswd -a charlie infra
User@localhost:~$ sudo gpasswd -a dave infra
```
4.
```console
User@localhost:~$ getent group
infra:x:1003:bob,charlie,dave

User@localhost:~$ grep infra /etc/group
infra:x:1003:bob,charlie,dave
```
5.
```console
User@localhost:~$ sudo usermod -m -d dev alice
User@localhost:~$ sudo usermod -m -d dev bob
User@localhost:~$ sudo usermod -m -d infra charlie
User@localhost:~$ sudo usermod -m -d infra dave
```
6.
```console
User@localhost:~$ sudo usermod alice -g dev
User@localhost:~$ sudo usermod bob -g dev
User@localhost:~$ sudo usermod charlie -g infra
User@localhost:~$ sudo usermod dave -g infra
```
7.
```console
User@localhost:~$ sudo chgrp -R dev /home/dev
User@localhost:~$ sudo chgrp -R infra /home/infra
User@localhost:~$ sudo chmod -R 060 /home//home/dev
User@localhost:~$ sudo chmod -R 060 /home/infra 
```
8.
```console
User@localhost:~$ sudo chmod 750 -R /home/dev
User@localhost:~$ sudo chmod 750 -R /home/infra
```
9.
```console
Non, un mot de passe est demandé. Le compte n'a pas encore été activé.
```
10.
```console
User@localhost:~$ sudo passwd alice
  New password : alice
  Retype new password : alice
User@localhost:~$ su alice
```
11.
```console
User@localhost:~$ id alice
uid=1002(alice). gid=1002(dev) groups=1002(dev)
```
12.
```console
User@localhost:~$ getent passwd 1003
Il s'agit de bob.
```
13.
```console
User@localhost:~$ grep dev /etc/group
L'id du groupe dev est 1002.
```
14.
```console
User@localhost:~$ grep 1002 /etc/group
Il s'agit du groupe dev.
```
15.
```console
User@localhost:~$ sudo gpasswd -d charlie infra
Reloving user charlie from group infra
Si l'on regarde les id de charlie, on voit qu'il appartient toujours au groupe infra.
```
16.
```console
User@localhost:~$ sudo chage dave -E 2021-06-01
User@localhost:~$ sudo chage dave -M 90 
User@localhost:~$ sudo chage dave -m 5
User@localhost:~$ sudo chage dave -W 14
User@localhost:~$ sudo chage dave -I 30
```
17.
```console
L'interpreteur de commande root est sudo.
```
18.
```console
Il correspond à un utilisateur sans droit, qui permet d'éxecuter quelque chose sans conséquence sur le reste.
```
19.
```console
Le mot de passe est mémorisé 15 minutes par la commande sudo.
Il s'agit de la commande sudo -k.
```

**Exercice 2**

