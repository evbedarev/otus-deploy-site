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
  }
}
