pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Get Kernel') {
      steps {
        script {
          try {
            KERNEL_VERSION = sh (script: "uname -r", returnStdout: true)
          } catch(err) {
            echo "CAUGHT ERROR: ${err}"
            throw err
          }
        }
      }
    }
    stage('Say Kernel') {
      steps {
        echo "${KERNEL_VERSION}"
      }
    }
    stage('Testing') {
      failFast true
      parallel {
        stage('Java 8') {
          agent { label 'jdk8' }
          steps {
            sh 'java -version'
            sleep time: 10, unit: 'SECONDS'
          }
        }
        stage('Java 9') {
          agent { label 'jdk9' }
          steps {
            sh 'java -version'
            sleep time: 20, unit: 'SECONDS'
          }
        }
      }
    }
  }
}
