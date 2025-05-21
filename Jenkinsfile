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
        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook(
                    playbook: 'playbookAns.yml',
                    inventory: 'inventory.ini'
                )
            }
        }
    }
}
