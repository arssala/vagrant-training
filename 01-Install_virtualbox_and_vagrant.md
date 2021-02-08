Vagrant Setup
==
## Introduction
Vagrant est un progiciel qui crée un environnement d'exploitation standardisé à l'aide de la technologie de virtualisation.

Vagrant fournit un outil de ligne de commande pour charger et gérer les systèmes d'exploitation virtuels. Nous utiliserons le fournisseur VirtualBox dans ce tutoriel.

Cet atelier vous guidera tout au long l'installation de Vagrant sur CentOS 7.

## Installer vagrant sur centos7
### Conditions préalables
Un compte utilisateur avec des privilèges sudo sur le  système CentOS 7
Accès à une ligne de commande / terminal (Menu> Applications> Utilitaires> Terminal)
Le gestionnaire de paquets yum, inclus par défaut
### Installez Vagrant sur CentOS
**Étape 1:** Actualiser les référentiels de logiciels
Dans une fenêtre de terminal, entrez la commande:
```
sudo yum update
```
Le gestionnaire de packages contactera les référentiels et actualisera les listes. Cela garantit que vous chargez les versions les plus récentes et les plus corrigées du logiciel.

**Étape 2:** Installez VirtualBox
Vagrant est un outil qui vous permet d'exécuter un système d'exploitation à l'intérieur d'un système d'exploitation. Il le fait en créant un environnement virtuel. Vagrant s'appuie sur une application tierce (comme VirtualBox) pour gérer les environnements virtuels.

1. Commencez par installer les dépendances pour VirtualBox. Entrez ce qui suit dans une fenêtre de terminal:
```
sudo yum –y install epel-release
sudo yum –y install gcc dkms make qt libgomp patch
sudo yum –y install kernel-headers kernel-devel binutils glibc-headers glibc-devel font-forge
```
2. Ensuite, ajoutez le référentiel de logiciels pour VirtualBox:
```
sudo cd /etc/yum.repo.d/
sudo wget http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo
```
3. Installez le logiciel VirtualBox:
```
sudo yum –y install VirtualBox-5.2
```
4. Vérifiez que VirtualBox est installé avec la commande:
```
Virtualbox
```
Le système devrait ouvrir une nouvelle fenêtre vous accueillant dans VirtualBox.

Il existe d'autres applications de virtualisation disponibles. Vous pouvez utiliser KVM, VMware ou tout autre type de logiciel hyperviseur .

**Étape 3:** Installez Vagrant sur CentOS
1. Ouvrez un navigateur Web et accédez à https://www.vagrantup.com/downloads.html . Cette page contient la version la plus récente du logiciel.

2. Dans une fenêtre de terminal, téléchargez le package d'installation en entrant:
```
sudo wget https://releases.hashicorp.com/vagrant/2.2.14/vagrant_2.2.14_x86_64.rpm
```
Le système doit télécharger le fichier d'installation. Ajustez le numéro de version et l'architecture du système (32 ou 64 bits) selon les besoins de votre système.

3. Installez Vagrant sur votre machine CentOS avec la commande:
```
sudo yum –y localinstall vagrant_2.2.14_x86_64.rpm
```
**Étape 4:** Vérifiez l'installation
Pour vérifier la réussite de l'installation, affichez la version de Vagrant avec la commande suivante:
```
vagrant --version
```
C'est un moyen rapide de s'assurer que l'installation s'est terminée avec succès.
