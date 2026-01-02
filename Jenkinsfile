pipeline {
    agent any
    
    tools {
        maven 'Maven3' 
    }
    
    // Ici, on demande à Jenkins de récupérer le secret
    environment {
        SLACK_LINK = credentials('slack-secret')
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build & Test') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Déploiement de l application...'
            }
        }
    }
    
    post {
        always {
            echo 'Envoi de la notification Slack...'
            // On utilise la variable $SLACK_LINK qui contient le secret caché
            sh "curl -X POST -H 'Content-type: application/json' --data '{\"text\":\"🚀 Projet DevOps EMSI : Le Build Jenkins est terminé avec succès ! Félicitations Chaimae !\"}' $SLACK_LINK"
        }
    }
}