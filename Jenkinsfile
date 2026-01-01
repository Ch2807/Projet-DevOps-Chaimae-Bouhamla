pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupère le code depuis GitHub (automatique via la config Jenkins, mais explicite c'est mieux)
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                // Compile et lance les tests via Maven
                // Utilise 'bat' car tu es sur Windows. Si erreur, remplace par 'sh'
                bat 'mvn clean package'
            }
        }

        stage('Archive') {
            steps {
                // Archive le fichier .jar généré (requis par la consigne)
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                // Simulation du déploiement (requis par la consigne optionnelle)
                echo 'Déploiement de l application...'
                // Ici on pourrait lancer: java -jar target/mon-app.jar
            }
        }
    }
    post {
        always {
            echo 'Fin du Pipeline.'
        }
    }
}