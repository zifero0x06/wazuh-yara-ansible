# Ajouter la détection de malwares pour Wazuh

Pour des terminaux dérivés de Linux Debian, il s'agit de mettre en oeuvre le module supplémentaire YARA pour Wazuh avec Ansible. 

Sur le terminal Linux cible :
1. Créer un utilisateur dédié pour Ansible
2. L'ajouter aux sudoers avec ```sudo visudo``` en ajoutant la ligne : ```ansible_user ALL=(ALL) NOPASSWD:ALL```

Sur le serveur Wazuh :
1. 	Créer un dossier Ansible qui contient le playbook et le fichier inventory
2. 	Créer une paire de clés public/privée pour mettre en oeuvre la connexion ssh aux terminaux administrés par Ansible sans mot de passe avec ```ssh-keygen -t rsa -b 4096```
3. 	Copier la clé sur les terminaux distants : ```ssh-copy-id -f ansible_user@192.168.0.X```
4. 	Utiliser Ansible avec ```ansible-playbook -i inventory.ini install_yara.yml```
