pipeline {
    agent any

    stages {
        stage('init') {
            steps {
                sh 'npm install'
                sh 'npx teamsfx -v'
            }
        }

        stage('build') {
            steps {
                sh 'cd tabs && npm install && npm run build'
                sh 'cd bot && npm install'
            }
        }

        stage('test') {
            steps {
                sh 'echo "run ut"'
            }
        }
    }
}