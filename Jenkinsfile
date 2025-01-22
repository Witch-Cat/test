pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("build") {
            steps {
                echo "Working Directory:"
                sh 'pwd && ls -l'
                sh 'mvn -v'
            }
        }
        stage("Build & Analyse avec SonarQube") {
            steps {
                script {
                    // Ajoutez le chemin correct si nécessaire
                    sh 'mvn -f pom.xml clean package sonar:sonar'
                }
            }
        }
        stage("deploy") {
            steps {
                echo 'Deploying application'
            }
        }
    }
}
