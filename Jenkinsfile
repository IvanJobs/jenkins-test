pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                bat 'npm install -g @microsoft/teamsfx-cli'
                bat 'teamsfx -v'
            }
        }
    }
}