pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') { 
            steps {
                sh 'echo Test'
            }
        }
        stage('Post Build') { 
            steps {
                archiveArtifacts artifacts: '*/*.war', followSymlinks: false
            }
        }
        stage('Deploy') { 
            steps {
                deploy adapters: [tomcat9(credentialsId: 'df4a9df4-8cea-49a1-998d-0ea7651ccc87', path: '', url: 'http://localhost:8080/')], contextPath: '/spark', onFailure: false, war: 'target/*.war'
            }
        }
    }
}