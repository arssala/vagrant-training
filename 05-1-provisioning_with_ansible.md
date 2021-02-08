Jekyll Box with the Ansible Provisioner
==
Cet exemple présente l'utilisation de base du provisionneur Ansible. Avant de pouvoir utiliser Ansible, vous devez l'installer.

## Box Source Code
Commencez par le répertoire vide:
```
# Host OS
$ cd folder/with/examples
$ mkdir vagrant-jekyll-ansible
```
Créez les deux fichiers: le Vagrantfile et le playbook.yml.
```
vi Vagrantfile
```
```
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.provision "ansible", playbook: "playbook.yml"
end
```
```
vi playbook.yml
```
```
- hosts: all
  become: yes
  tasks:
  — name: Update apt
    apt: update_cache=yes
  — name: Install items
    apt:
      name: "{{ item }}"
      state: present
    loop:
    - ruby
    - ruby-dev
    - make
    - build-essential
    - lynx
  - name: edit .bashrc
    become: no
    shell: |
      echo "export GEM_HOME=$HOME/gems" >> /home/vagrant/.bashrc
      echo "export PATH=$HOME/gems/bin:$PATH" >> /home/vagrant/.bashrc
      source /home/vagrant/.bashrc

  - name: Install Jekyll
    shell: 'gem install jekyll'
```

Pour activer le provisionneur Ansible, le Vagrantfile contient les éléments suivants:
  config.vm.provision "ansible", playbook: "playbook.yml"

### First Run of the Ansible Provisioner
Pour démarrer la VM, exécutez ces commandes (il leur faudra un peu de temps, peut-être même une demi-heure, pour terminer):
```
# Host OS
$ cd vagrant-jekyll-ansible
$ vagrant up
```
## Exercice

Créez le projet flowers-vagrant-jekyll-ansible, qui devrait utiliser le box vagrant-jekyll-ansible.
