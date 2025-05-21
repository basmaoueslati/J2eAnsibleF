pipeline {
    agent any
    tools {
           jdk 'jdk11'
    }
    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://13.38.26.11:8080/')], contextPath: null, war: '**/*.war'                            }
        }
    }
}
