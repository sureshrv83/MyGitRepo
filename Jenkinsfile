pipeline {
agent {
    docker {
        image 'maven:3-alpine'
        args '-v /root/.m2:/root/.m2'
    }
    environment {
           AUTH_DISPLAY = 'MAIN'
           MYNAME = 'MAIN'
    }
    stages {
  stage('build') {
            steps {
            sh 'echo $AUTH_DISPLAY'
            sh 'echo $MYNAME'
                sh 'cd /Users/Shared/Jenkins/Home/workspace/JenkinsConnect/gitconnect/webapp-master;mvn -B -DskipTests clean package'
            }
        }
        stage('deploy') {
            steps {

            sh 'echo $AUTH_DISPLAY'
            sh 'echo $MYNAME'
                sh 'cd /Users/Shared/Jenkins/Home/workspace/JenkinsConnect/gitconnect/webapp-master;mvn tomcat7:redeploy'
            }
        }
        stage('input'){
        environment {
        AUTH_DISPLAY = 'INSIDE STAGE'
          MYNAME = 'AVYU'}
            steps{
            sh 'echo $AUTH_DISPLAY'
            sh 'echo $MYNAME'
            input 'Does it need to done ? yes or no'
            }
        }
    }
    post {
    success {
        slackSend channel: '#jenkinsconnect',
                  color: 'good',
                  message: "The pipeline ${currentBuild.fullDisplayName} completed successfully."
    }
}
}
