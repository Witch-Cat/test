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
        
        stage("deploy") {
            steps {
                echo 'Deploying application'
            }
        }
    }
}

