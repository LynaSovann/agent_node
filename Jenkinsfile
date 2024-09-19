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
        echo "🚀 Deploying the application"
        script {
          def containerExists = sh(script: "docker ps -a -q -f name=${APP_NAME}", returnStdout: true).trim()
          if(containerExists) {
            echo "Stopping and removing existing container"
            sh "docker stop ${APP_NAME}"
            sh "docker rm ${APP_NAME}"
          }
        }
        sh " docker run --name ${APP_NAME} -d -P ${APP_NAME} "
        sh " docker ps " 
      }
    }



  }
  
}
