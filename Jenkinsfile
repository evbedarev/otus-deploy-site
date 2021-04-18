def ansible_ver = "hellow from jenkins"
pipeline {
  agent any
  stages {
    stage('hellow') {
      steps {
        script {
          def cur_cluster = sh(script:"kubectl config current-context", returnStatus: true)
          sh "echo ${cur_cluster}"
          sh "echo ${cur_cluster}"
        }
      }
    }
    stage('deploy') {
      steps {
        ansiColor('xterm') {
            ansiblePlaybook colorized: true, credentialsId: 'ansible_user', inventory: 'hosts', limit: '', playbook: 'site.yml', sudoUser: null, vaultCredentialsId: 'vault_password', extras: '-vv -e "ansible_pyhton_interpreter=/usr/bin/pyhton need_create_cluster=${NEED_CREATE_CLUSTER}"'
        }
      }
    }
  }
}
