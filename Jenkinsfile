pipeline {
    agent any
    tools {
        maven 'Maven 3.8.1'  // Use the actual name of the Maven installation in Jenkins
    }

    environment {
        SONARQUBE = 'SonarQube'  // Ensure this matches the name of the SonarQube server configuration in Jenkins
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
                def mvn = tool 'Maven 3.8.1'  // Replace with your Maven version name
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
