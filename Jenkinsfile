pipeline {
  agent none

  stages {
    
    stage('Build & SonarQube Analysis') {
      agent any
      steps {
        withSonarQubeEnv('My SonarQube Server'){
          bat 'mvn clean package sonar:sonar'
        }
      }
    }

    stage('Quality Gate') {
      steps {
        timeout(time: 1, unit: 'HOURS'){
          def qg = waitForQualityGate()
          if(qg.status != 'OK') error "Pipeline aborted, quality gate failure: ${qg.status}"
        }
      }
    }
  }
}
