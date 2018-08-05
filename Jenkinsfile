pipeline {
    agent any
    stages {
    environment {
           AUTH_DISPLAY = 'MAIN'
           MYNAME = 'MAIN'
    }
        stage('build') {
            steps {
            sh 'echo $AUTH_DISPLAY'
            sh 'echo $MYNAME'
                sh 'cd /Users/Shared/Jenkins/Home/workspace/JenkinsConnect/gitconnect/webapp-master;/Applications/apache-maven-3.5.4/bin/mvn clean package'
            }
        }
        stage('deply') {
            steps {
            sh 'echo $AUTH_DISPLAY'
            sh 'echo $MYNAME'
                sh 'cd /Users/Shared/Jenkins/Home/workspace/JenkinsConnect/gitconnect/webapp-master;/Applications/apache-maven-3.5.4/bin/mvn tomcat7:redeploy'
            }
        }
        stage('input'){
        AUTH_DISPLAY = 'INSIDE STAGE'
        MYNAME = 'AVYU'
            steps{
            sh 'echo $AUTH_DISPLAY'
            sh 'echo $MYNAME'
            input 'Does it need to done ? yes or no'
            }
        }
    }
}
