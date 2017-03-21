pipeline {
  agent any
  stages {
    stage('Clean') {
      steps {
        echo 'Starting build'
      }
    }
    stage('Compile') {
      steps {
        sh 'gradle'
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test": {
            echo 'Testing'
            
          },
          "Publish": {
            archiveArtifacts 'target'
            
          }
        )
      }
    }
    stage('') {
      steps {
        mail(subject: 'Report', body: 'Failed', from: 'kpritam@thoughtworks.com', to: 'kpritam@thoughtworks.com')
      }
    }
  }
}