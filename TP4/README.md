# inventaire : les différents formats - variables : ansible_connection, ansible_port, env

```bash

mkdir TP4 && cd ./TP4 # création d'un répertoire de travail et déplacement

ansible-inventory -i hosts.ini -y --list > hosts.yaml # création d'un fichier format yaml depuis le fichier ini 

ansible -i hosts.ini client -m ping # test de l'inventaire de la machine client ping

ansible -i hosts.yaml prod -m ping # test de l'inventaire de la machine prod ping -i pour l'appel des différents inventaires

ansible -i hosts.ini all -m copy -a "dest=/home/vagrant/toto.txt content='bonjour eazytrining {{ env }} '" # copie d'un fichier toto.txt, -a transfert d'un fichier vers plusieurs serveurs 

ansible all --list-hosts # lister les hosts, différentes machines

ansible prod --list-hosts 

ansible client1 --list-hosts 

ansible-inventory --host  client1 

ansible -i hosts.ini prod -m ping # diférents tests 

ansible -i hosts.ini client -m ping 

ansible -i hosts.ini client1 -m ping 

ansible-inventory --graph  # inventaire sous forme de graph

ansible -i all  -m ping 

ansible -i hosts all -m ping 

ansible -i hosts.ini all -m ping 

# transformation du fichier yaml en json depuis une commande python

python3 -c 'import sys, yaml, json; json.dump(yaml.load(sys.stdin, Loader=yaml.FullLoader), sys.stdout, indent=4)' < hosts.yaml > hosts.json 

ansible all -m ping 

ansible -i hosts.json all -m ping 

ansible -i hosts.yaml all -m ping 

python3 -c 'import sys, yaml, json; json.dump(yaml.load(sys.stdin, Loader=yaml.FullLoader), sys.stdout, indent=4)' < hosts.yaml > hosts.json 

ansible -i hosts.json all -m ping

```
