pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'echo $AUTH_DISPLAY'
        sh 'echo $MYNAME'
        sh 'whoami'
        sh 'docker version'
        sh 'cd ${WORKSPACE}/webapp-master;mvn -B -DskipTests clean package'
      }
    }
    stage('deploy') {
      steps {
        sh 'echo $AUTH_DISPLAY'
        sh 'echo $MYNAME'
        sh 'cd ${WORKSPACE}/webapp-master;mvn tomcat7:redeploy'
      }
    }
    stage('input') {
      environment {
        AUTH_DISPLAY = 'INSIDE STAGE'
        MYNAME = 'AVYU'
      }
      steps {
        sh 'echo $AUTH_DISPLAY'
        sh 'echo $MYNAME'
        input 'Does it need to done ? yes or no'
      }
    }
    stage('Test') {
      steps {
        echo 'suresh'
      }
    }
  }
  tools {
    maven 'Maven 3.3.9'
    jdk 'jdk8'
    git 'git9'
  }
  environment {
    AUTH_DISPLAY = 'MAIN'
    MYNAME = 'MAIN'
  }
  post {
    success {
      slackSend(channel: '#jenkinsconnect', color: 'good', message: "The pipeline ${currentBuild.fullDisplayName} completed successfully.")

    }

  }
}