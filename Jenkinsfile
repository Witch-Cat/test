pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    environment {
        SONAR_HOST_URL = 'http://172.17.0.3:9000' // Remplacez par l'URL correcte
    }
    stages {
        stage("build") {
            steps {
                sh 'mvn -v'
            }
        }
        stage("Build & Analyse avec SonarQube") {
            steps {
                script {
                    sh 'mvn clean package sonar:sonar -Dsonar.host.url=$SONAR_HOST_URL'
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
