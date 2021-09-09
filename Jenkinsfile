pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                bash 'npm install -g @microsoft/teamsfx-cli'
                bash 'teamsfx -v'
            }
        }
    }
}