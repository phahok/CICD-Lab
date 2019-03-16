# CICD
Material do ambiente do curso de Integração e Entrega Continua com Git, Jenkins, Nexus e Sonar


## Aula00 - Apresentando ambiente com Vagrant
## Aula01 - Iniciando ambiente com maquina repo
### Maquina Host	
sudo vagrant up repo --provision
### Maquina Repo
Instalando Gitlab-CE
```sh
# curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | sudo bash
```
Configurando Gitlab-CE
```sh
# vim /etc/gitlab/gitlab.rb

...
alertmanager['enable'] = false
external_url 'http://192.168.99.10'
gitlab_monitor['enable'] = false
node_exporter['enable'] = false
postgres_exporter['enable'] = false
prometheus['enable'] = false
redis_exporter['enable'] = false
...
```
Carregando novas configurações
```sh
# gitlab-ctl reconfigure
```

## Aula02 - Iniciando maquina pipeline
Iniciando a maquina pipeline via vagrant.
```sh
$ vagrant up pipeline --provision
```
### Instalando serviços na maquina pipeline
Instalando Jenkins
```sh
# curl http://pkg.jenkins-ci.org/redhat/jenkins.repo -o /etc/yum.repos.d/jenkins.repo
# rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
# yum install jenkins
``` 
