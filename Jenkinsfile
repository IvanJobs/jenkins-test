pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                sh 'npm install'
                sh 'npx teamsfx -v'
            }
        }
    }
}