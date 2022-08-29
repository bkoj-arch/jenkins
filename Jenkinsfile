pipeline {
  agent any
  stages {
    stage('BUILD') {
      steps {
        sh 'mvn clean install'
      }
    }

    stage('Test') {
      steps {
        sh 'echo Test'
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
        sh 'rm -r  /var/lib/tomcat9/webapps/spark*'
        sh 'cp target/*.war /var/lib/tomcat9/webapps/'
      }
    }

  }
}