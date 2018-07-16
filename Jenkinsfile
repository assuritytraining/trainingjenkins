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
        message "Which Version?"
        ok "Deploy"
        parameters {
            choice(name: 'APP_VERSION', choices: "v1.1\nv1.2\nv1.3", description: 'What to deploy?')
        }
      }
      steps {
        echo "Deploying ${APP_VERSION}."
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
  post {
    aborted {
      echo 'Why didn\'t you push my button?'
    }
  }
}
