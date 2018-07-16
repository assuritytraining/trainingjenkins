pipeline {
  agent {
    label 'jdk9'
  }
  stages {
    stage('Hello World') {
      steps {
        echo 'Hello World'
        sh 'java -version'
      }
    }
  }
}