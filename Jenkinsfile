pipeline {
  agent {
    label 'ubuntu-agent-01'
  }
  environment {
    APP_NAME="t-twister"
  }

  stages {

    stage("build") {
      steps {
        sh "docker build ${APP_NAME} ."
      }
    }

    stage("deploy") {
      steps {
        sh " docker run --name ${APP_NAME} -d -P ${APP_NAME} "
      }
    }
  }
  
}
