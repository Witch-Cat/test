pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    environment {
        SONAR_HOST_URL = 'http://172.17.0.3:9000'
        SONAR_TOKEN = credentials('sqa_81452abf552c5c176c1390771264634377adb38e') // Jeton sécurisé dans Jenkins
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
                    sh 'mvn clean package sonar:sonar -Dsonar.host.url=$SONAR_HOST_URL -Dsonar.token=$SONAR_TOKEN'
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
