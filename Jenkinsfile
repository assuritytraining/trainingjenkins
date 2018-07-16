pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Hello World') {
      steps {
        echo "Hello ${NAME}!"
        sh 'java -version'
        echo "User: ${CREDS_USR}\nPass: ${CREDS_PSW}"
      }
    }
  }
  environment {
    NAME = 'Testing'
    CREDS = credentials('testing')
  }
}