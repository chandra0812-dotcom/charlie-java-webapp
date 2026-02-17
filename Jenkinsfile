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
          tomcat9(
            credentialsId: 'tomcat-creds',
            url: 'http://100.31.102.136:8080/manager/text'
          )
        ],
        contextPath: 'simple-webapp',
        war: 'target/simple-webapp.war'
      }
    }
  }
}

