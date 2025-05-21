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
                withCredentials([sshUserPrivateKey(credentialsId: 'ansible_ssh_key', keyFileVariable: 'SSH_KEY')]) {
                    sh "ansible-playbook -i inventory.ini playbook.yml --private-key=$SSH_KEY"
            }
        }
    }
}
}
