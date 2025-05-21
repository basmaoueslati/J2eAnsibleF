pipeline {
    agent any
    tools {
           jdk 'jdk11'
    }
    vars:
        INVENTORY : 'inventory.ini'
        PLAYBOOK : 'playbook.yml'
    
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
                sh "ansible-playbook -i ${INVENTORY} ${PLAYBOOK}"
            }
        }
    }
}
