node {
  stage('SCM') {
    git 'https://github.com/Fermonx/CI_2'
  }
  stage('SonarQube analysis') {
    def scannerHome = tool 'SONAR_SCANNER_HOME';
    withSonarQubeEnv('CI_Test') {
      bat "${scannerHome}/bin/sonar-scanner"
    }
  }
}
