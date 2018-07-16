pipeline {
  agent {
    label 'jdk8'
  }
  stages {
      stage('Checkpoint') {
         agent none
         steps {
            checkpoint 'Checkpoint'
         }
      }
      stage('Deploy') {
        agent {
          label 'jdk8'
        }
        steps {
          echo 'Deploying....'
        }
      }
  }
}
