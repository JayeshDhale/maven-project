pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prakashk0301/maven-project'
        }
  }
    {
        stage ('Compile Stage') {
            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }
		stage ('build && SonarQube analysis') {
steps {

withSonarQubeEnv('sonar') {
withMaven(maven : 'LocalMaven') {
sh 'mvn clean package sonar:sonar'
} } } }         
}
}
