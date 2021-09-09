pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                sh 'npm install -g @microsoft/teamsfx-cli'
                sh 'teamsfx -v'
            }
        }
    }
}