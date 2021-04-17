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
          withCredentials([string(credentialsId: 'vault_password', variable: 'VAULT_PASS')]) {
            script {
              sh "echo $VAULT_PASS"
            }
            ansiblePlaybook colorized: true,
                inventory: "hosts",
                playbook: "site.yml",
                vaultCredentialsId: "$VAULT_PASS"
          }
        }
      }
    }
  }
}
