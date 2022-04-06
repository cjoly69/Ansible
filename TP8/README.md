# Déploiement d'un Wordpress depuis Ansible (ansible-galaxy)

* Création d'un cluster (ansible + client) 
Recupérez votre code provenant du TP-7
* Création d'un playbook wordpress.yml afin de déployer wordpress 
    -> sous forme de conteneur docker (cela sous entend l'installation de Docker si le role ne le fait pas)
    -> sur le client à l’aide du rôle https://github.com/diranetafen/ansible-role-containerized-wordpress.git
* Lancement du playbook et vérification

_Vous pouvez exposer wordpress sur le port externe de votre choix, 80 ou 8080 ou autre_

Pour récupérer mes roles définis dans un fichier roles/requirements.yml, je tape la commande : 
```bash
ansible-galaxy install -r roles/requirements.yml
```

En pre_tasks du playbook, on aura : 

```yaml
  pre_tasks:
    - name: create www data
      user: 
        name:  www-data
        state: present
    - name: Install docker-compose on target
      get_url:
        url: "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-Linux-x86_64"
        dest: /usr/bin/docker-compose     
        mode: 'u+x,g+x'
```
