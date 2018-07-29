pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'cd /Users/sureshramayanam/Documents/myGitRepo/webapp-master'
                sh '/Applications/apache-maven-3.5.4/bin/mvn clean package'
            }
        }
    }
}
