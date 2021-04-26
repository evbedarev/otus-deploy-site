# Проектная работа

1. Развертывание происходит с помощью Jenkins.
- Jenkinsfile запускает ansible, подставляет пароль от vault хранящийся в Credentials.
- Сборка параметризована, параметр NEED_CREATE_CLUSTER, в зависимости от значения запускается или нет развертывание gke кластера.


2. asnible
- Все пароли/сертификаты храняться в ansible-vault.
- Роль create_gke развертывает кластер и 2х нод для приложения и 4х нод для инфраструктуры, отмечает их соответсвующими taints. Параметры кластера и нод беруться из переменных.

- Роль deploy_ingress равертывает 2 пода ингресса на ноды с taint "infra" и podAntiAffinity для разноса экземпляров на разные ноды. Так же создается secret с сертификатами ingress.

- Роль monitoring равертывает prometheus, grafana, node-exporter на ноды с taint "infra". Так же деплоиться ингресс для графаны и череза api графаны постим дашборды для nginx-ingress & node-exporter.

- Роль logging развертывает elasticsearch и fluent-bit  на ноды с taint "infra", kibana. Fluent-bit собирает логи с nginx-ingress и отправляет в эластик.
