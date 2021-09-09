pipeline {
    agent {
        docker {
            image 'ubuntu:latest'
            label 'my-defined-label'
        }
    }

    stages {
        stage('init') {
            steps {
                bat 'npm install -g @microsoft/teamsfx-cli'
            }
        }
    }
}