def ansible_ver = "hellow from jenkins"
pipeline {
  agent any
  stages {
    stage('crete_gke_cluster') {
      steps {
        ansiColor('xterm') {
            ansiblePlaybook colorized: true, credentialsId: 'ansible_user', inventory: 'hosts',tags:"install_gke", limit: '', playbook: 'site.yml', sudoUser: null, vaultCredentialsId: 'vault_password', extras: '-vv -e "ansible_pyhton_interpreter=/usr/bin/pyhton need_create_cluster=${NEED_CREATE_CLUSTER}"'
        }
      }
    }
    stage('deploy infra') {
      steps {
        ansiColor('xterm') {
            ansiblePlaybook colorized: true, credentialsId: 'ansible_user', inventory: 'hosts',tags:"deploy_infra", limit: '', playbook: 'site.yml', sudoUser: null, vaultCredentialsId: 'vault_password', extras: '-vv -e "ansible_pyhton_interpreter=/usr/bin/pyhton need_create_cluster=${NEED_CREATE_CLUSTER}"'
        }
      }
    }
    stage('deploy app') {
      steps {
        ansiColor('xterm') {
            ansiblePlaybook colorized: true, credentialsId: 'ansible_user', inventory: 'hosts',tags:"deploy_application", limit: '', playbook: 'site.yml', sudoUser: null, vaultCredentialsId: 'vault_password', extras: '-vv -e "ansible_pyhton_interpreter=/usr/bin/pyhton need_create_cluster=${NEED_CREATE_CLUSTER}"'
        }
      }
    }
  }
}
