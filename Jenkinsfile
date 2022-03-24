pipeline{
  agent any;
  tools {
    
  }
  parameters{
    booleanParam description:
  }
  stages {
    stage('Compilo') {
      echo 'Pedir a maven que compile'
      sh 'mvn compile'
    }
    stage('Pruebo') {
      steps {
        echo 'Pedir a maven que testee'
      }
      post {
      always {
        junit allowEmptyResults: true, testResults: 'target/*reports.xml'
      }
    }
    stage('Empaquetar') {
      steps {
      echo 'Pedir a maven que empaquete'
      sh 'mvn package'
      }
      post{
        always {
          echo 'Guardo el WAR'
          archiveArtifacts artifacts: '', followSymlinks: false
        }
      }
     }
  }
  post {
    always {
      echo 'impia procesos y logs'
    }
  }
}
