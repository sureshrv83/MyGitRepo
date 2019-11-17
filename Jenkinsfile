pipeline {
  agent any
  stages {
    stage('test') {
      parallel {
        stage('test1') {
          steps {
            sh 'echo suresh'
          }
        }
        stage('test2') {
          steps {
            echo 'Avyu'
            sh 'ls -ltr'
          }
        }
      }
    }
  }
}
