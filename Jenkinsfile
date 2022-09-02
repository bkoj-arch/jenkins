pipeline {
  agent { label 'agent1' }
  stages {
    stage('BUILD') {
      steps {
        sh 'mvn clean install'
      }
    }

    stage('POST BUILD') {
      steps {
        archiveArtifacts(artifacts: 'target/*.war', onlyIfSuccessful: true)
      }
    }

    stage('DEPLOY') {
      steps {
deploy adapters: [tomcat9(credentialsId: 'df4a9df4-8cea-49a1-998d-0ea7651ccc87', path: '', url: 'http://172.17.0.3:8080')], contextPath: '/spark', onFailure: false, war: '*/*.war'      
	}
    }

  }
}
