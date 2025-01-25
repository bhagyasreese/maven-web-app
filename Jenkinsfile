pipeline {
    agent any
    tools{
        maven 'maven-3.6.3'
    }

    stages {
        stage('GIT Clone') {
            steps {
            git credentialsId: 'Github_username_password', url: 'https://github.com/sandeepkumarmekapothula/maven-web-app.git'
            }
        }

        stage('MAVEN Build') {
            steps {
            sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://34.219.78.189:8080')], contextPath: null, war: '**/*.war'
                 }
        }
    }
}
