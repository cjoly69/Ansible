# Deploiement d'une image   docker via Ansible from scratch

image de mario  https://hub.docker.com/r/pengbai/docker-supermario utilisée

Dans le répoertoire TP_mario, on reprend l'inventaire du TP 5.
    - prod.yml
    - group_vars/prod.yaml

Il faut créer trois playbooks :

    - docker.yml permettant d'installer docker avec les étapes suivantes
        * Le play doit avoir un tag docker
        * Installation de python3 sur la cible  ainsi que des dependances suivantes : 
            - yum-utils
            - device-mapper-persistent-data
            - lvm2
        * Installation de python pip (pip3) sur la  cible
            + Il suffit de download le scrpit https://bootstrap.pypa.io/get-pip.py et l'exécuter avec python3
            + on pourra utiliser les modules get_url et command ou shell
        * Installation de la librairie (sdk) docker pour python à l'aide de pip3. son nom est docker-py
            Se référer à la documentatin du module docker_container, au niveau des requirements
            On pourra utiliser le module pip de ansible
            Attention a l'exécutable utilisé par pip, il faudra trouver un moyen de lui dire d'utiliser le bon executable
        * Installation de docker
            + repos docker centos : https://download.docker.com/linux/centos/docker-ce.repo
            + nom du package : docker
            + se référer à la documentation d'installation de docker si besoin
    - mario.yml permettant de déployer le conteneur Mario  
        * le module docker_container sera utile  
        * image docker : https://hub.docker.com/r/pengbai/docker-supermario
        * La variable ansible_python_interpreter: /usr/bin/python3 pourrait etre utile
        * Le play doit avoir un tag mario
    - deploy_mario.yaml : 
        * Il fait simplement appel aux deux playbook précédents

        ```
        ansible-playbook deploy_mario.yml
        ```