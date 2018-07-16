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
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
        echo "${params.Greeting}, welcome!"
      }
    }
    stage('Deploy') {
      options {
        timeout(time: 30, unit: 'SECONDS')
      }
      input {
        message 'Hey user! Shall we continue?'
      }
      steps {
        echo 'Continuing with deployment'
      }
    }
  }
  environment {
    NAME = 'Testing'
    CREDS = credentials('testing')
    TEST_USER = credentials('test-user')
  }
  parameters {
    string(name: 'Greeting', defaultValue: 'Hello', description: 'Name yourself!')
  }
}