pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/JayeshDhale/maven-project'
        }
  }
    {
        stage ('build && SonarQube analysis') {
steps {

withSonarQubeEnv('sonar for jenkins') {
withMaven(maven : 'LocalMaven') {
sh 'mvn clean package sonar:sonar'
} } } }
}
}
