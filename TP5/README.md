```bash
mkdir TP5 && cd ./TP5 
mkdir webapp 
ls 
cd webapp/ 
touch prod.yml 
mkdir group_vars 
ansible all -i prod.yml -m ping 
ansible all  -m ping # après avoir ajouter un ansible.cfg à la racine de mon dossier (route le prod.yml) avec inventory = $PWD/prod.yml 
ansible-playbook nginx.yml -C # check avant de lancer le playbook 
ansible-playbook nginx.yml # lancement du playbook 
```