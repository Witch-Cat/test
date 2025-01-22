pipeline {
    agent any
    tools {
        maven 'Maven'  // Use the default 'Maven' tool configured in Jenkins
    }

    environment {
        SONARQUBE = 'SonarQube'  // Ensure this matches your SonarQube configuration in Jenkins
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
                def mvn = tool 'Maven'  // Use the default 'Maven' tool
                withSonarQubeEnv(SONARQUBE) {
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
