pipeline {
    agent any

    tools {
        maven "Maven"
    }

    stages {
        stage('verify'){
            steps {
                sh 'mvn -v'
            }
        }
        
        stage('compile'){
            steps{
                sh 'mvn clean compile'
            }
        }
        
        stage('test'){
            steps {
                sh 'mvn test'
            }
            post {
               success {
            		junit '**/target/surefire-reports/TEST-*.xml'
            	}
            }
        }
    }
    post {
        success {
            slackSend channel: 'jenkins-training', color: '#62F30A', message: 'Build success ! Souleymane', teamDomain: 'devinstitut', tokenCredentialId: 'slack-token-bon'
            
        }
        failure {
            slackSend channel: 'jenkins-training', color: '#F30A23', message: 'Build failed ! Souleymane', teamDomain: 'devinstitut', tokenCredentialId: 'slack-token-bon'
        
        }
    }
}