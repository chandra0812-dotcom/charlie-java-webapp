pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout Code') {
            steps {
                    git branch: 'main',
            url: 'https://github.com/chandra0812-dotcom/charlie-java-webapp.git'
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
                        url: 'http://http://34.235.138.104/:8080'
                    )
                ],
                contextPath: 'simple-webapp',
                war: 'target/simple-webapp.war'
            }
        }
    }
}
