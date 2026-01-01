pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                // UTILISATION DE sh AU LIEU DE bat POUR LINUX/DOCKER
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