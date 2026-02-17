pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/<your-username>/simple-java-webapp.git'
            }
        }

        stage('Build WAR') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat10(
                        credentialsId: 'tomcat-cred',
                        path: '',
                        url: 'http://<Tomcat-IP>:8080'
                    )
                ],
                contextPath: 'simple-webapp',
                war: 'target/simple-webapp.war'
            }
        }
    }
}
