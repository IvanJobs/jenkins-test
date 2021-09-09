pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                sh 'pwd'
                sh 'ls -lh'
                sh 'npm install'
                sh 'npx teamsfx -v'
            }
        }
    }
}