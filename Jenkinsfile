pipeline {
    agent any
    
    // Configuration de l'outil Maven (qu'on a installé à l'étape précédente)
    tools {
        maven 'Maven3' 
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Récupération du code depuis GitHub
                checkout scm
            }
        }
        
        stage('Build & Test') {
            steps {
                // Compilation et tests (commande sh pour Linux/Docker)
                sh 'mvn clean package'
            }
        }
        
        stage('Archive') {
            steps {
                // Archivage du fichier .jar généré
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        
        stage('Deploy') {
            steps {
                // Simulation du déploiement
                echo 'Déploiement de l application...'
            }
        }
    }
    
    post {
        always {
            echo 'Envoi de la notification Slack...'
            // Envoi du message via ton Webhook Slack
            sh "curl -X POST -H 'Content-type: application/json' --data '{\"text\":\"🚀 Projet DevOps EMSI : Le Build Jenkins est terminé avec succès ! Félicitations Aya !\"}' https://hooks.slack.com/services/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"
        }
    }
}