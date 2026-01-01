pipeline {
    agent any
    
    // Ajout de la configuration des outils
    tools {
        maven 'Maven3' 
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build & Test') {
            steps {
                // Jenkins va maintenant utiliser le mvn configuré
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
            echo 'Fin du Pipeline.'
        }
    }
}