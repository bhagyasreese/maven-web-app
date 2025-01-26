pipeline {
    agent any
    tools{
        maven 'maven-3.6.3'
    }

    stages {
        stage('GIT Clone') {
            steps {
            git credentialsId: 'Github_username_password', url: 'https://github.com/bhagyasreese/maven-web-app.git'
            }
        }

        stage('MAVEN Build') {
            steps {
            sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://65.0.71.59:8080/')], contextPath: null, war: '**/*.war'
                 }
        }
    }
}
