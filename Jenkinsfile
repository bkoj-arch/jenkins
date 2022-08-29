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
                sh 'echo test'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'pwd'
                sh 'echo fin' 
            }
        }
    }
}