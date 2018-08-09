    pipeline {

    agent {
      node {
        label 'agent1'
      }
    }


    environment {
      AUTH_DISPLAY = 'MAIN'
      MYNAME = 'MAIN'
    }

        stages {
      stage('build') {
      agent {
          docker {
            /*
             * Reuse the workspace on the agent defined at top-level of Pipeline but run inside a container.
             * In this case we are running a container with maven so we don't have to install specific versions
             * of maven directly on the agent
             */
            reuseNode true
            image 'maven:3.5.0-jdk-8'
          }
        }
                steps {
                sh 'echo $AUTH_DISPLAY'
                sh 'echo $MYNAME'
                sh 'whoami'
                sh 'docker version'
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
