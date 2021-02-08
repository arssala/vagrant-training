Port Forwarding
==

Port forwarding nous permet de spécifier des ports sur la machine Guest à partager via un port sur la machine hôte. Cela nous permet d'accéder à un port sur notre machine hôte, mais en fait, tout le trafic réseau est redirigé vers un port spécifique de la machine invitée, via TCP ou UDP.

Configurons une redirection de port afin que nous puissions accéder à Jekyll dans notre Guest en configurant Vagrantfile:

Pour reconfigurer la redirection de port, vous devez éditer le Vagrantfile comme ceci:
```
# Host
$ vi ~/corporate-blog/Vagrantfile
```
Modifiez son contenu en ajoutant une redirection de port. Le port hôte 8080 doit être redirigé vers le port invité 4000.

C'est le but de l' entrée config.vm.network
```
Vagrant.configure(2) do |config|
  config.vm.box = "first-box-jekyll"
  config.vm.network :forwarded_port, guest: 4000, host: 8080, host_ip: "127.0.0.1"
end
```
Pour appliquer les nouvelles modifications, vous devez recharger le système d'exploitation invité avec ceci:
```
# Host
$ vagrant reload
```
Après avoir redémarré le système, vous devez redémarrer le serveur Jekyll intégré:
```
# Host
$ vagrant ssh
```
```
# Guest
$ cd /vagrant
$ jekyll serve -H 0.0.0.0 --detach
```
Maintenant, si vous exécutez le navigateur Web sur votre hôte et accédez à http://localhost:8080, vous serez redirigé vers  le port numéro 4000 de la VM.


### Exercices
1. Créez un nouveau box CentOS7 contenant nginx
