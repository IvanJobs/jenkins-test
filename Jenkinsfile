pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                npm install -g @microsoft/teamsfx-cli
                teamsfx -v
            }
        }
    }
}