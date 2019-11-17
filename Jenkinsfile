pipeline {
  agent any
  stages {
    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'echo suresh'
          }
        }
        stage('parallel step') {
          steps {
            echo 'Avyu'
            sh 'ls -ltr'
          }
        }
      }
    }
  }
}