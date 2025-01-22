pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    environment {
        SONAR_HOST_URL = 'http://172.17.0.3:9000'
        SONAR_TOKEN = credentials('sqa_5decfdda42e256676b49419a5538d6e47d3cdc84') // Jeton sécurisé dans Jenkins
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
