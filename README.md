**All templates were created by [vdiogov](https://github.com/vdiogov/glpi-conteiner).**

STEP 1: install with helm:
kubectl create namespace glpi
helm repo add glpi-chart https://zepfred.github.io/glpi-chart/
helm install glpi-helm -n glpi glpi-chart/glpi

STEP 2: expose service:

    kubectl port-forward -n glpi glpi-helm-service 80:80

STEP 3: get db password (in windows use gitbash to decode base64):

    kubectl get secret -n glpi glpi-helm-mariadb-secret -o jsonpath='{.data.password}' | base64 --decode

STEP 4: acess & configure

    http://localhost

Setup >

DB config (you can set user and password in docker-compose file), default is:

    HOST = glpi-helm-mariadb-service

    user = user_glpi

    password = (STEP 3)

DB Select >

    glpi
