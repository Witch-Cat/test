pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    
    stages {
        stage("build") {
            steps {
                sh 'mvn -v'
            }
        }
        
        stage('SCM') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                def mvn = tool 'Default Maven'
                withSonarQubeEnv() {
                    sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=test -Dsonar.projectName='test'"
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
