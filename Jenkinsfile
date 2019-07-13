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

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn install'
                }
            }
        }
        stage ('deploy to dev') {
             steps {
                  sshagent (credentials: ['e2341f5c-2e83-4e46-ab03-6f5279becc8e']) {
                sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.6.30:/var/lib/tomcat/webapps'
} } }

         
}
}
