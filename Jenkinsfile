pipeline {
  agent { label 'agent1' }
  stages {
    stage('BUILD') {
      steps {
        sh 'mvn clean install'
      }
    }

    stage('POST BUILD') {
      agent any
      steps {
        archiveArtifacts(artifacts: '*/*.war', onlyIfSuccessful: true)
      }
    }

    stage('DEPLOY') {
      steps {
        sh 'cp target/*.war /var/lib/jenkins/deploy/spark.war'
      }
    }

  }
}
