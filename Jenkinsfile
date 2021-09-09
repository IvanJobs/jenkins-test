pipeline {
    agent {
        docker {
            image 'ubuntu:latest'
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