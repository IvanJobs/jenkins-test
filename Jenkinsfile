pipeline {
    agent any

    environment {
        AZURE_ACCOUNT_NAME = credentials('AZURE_ACCOUNT_NAME')
        AZURE_ACCOUNT_PASSWORD = credentials('AZURE_ACCOUNT_PASSWORD')
        M365_ACCOUNT_NAME = credentials('M365_ACCOUNT_NAME')
        M365_ACCOUNT_PASSWORD = credentials('M365_ACCOUNT_PASSWORD')
        AZURE_SUBSCRIPTION_ID = credentials('AZURE_SUBSCRIPTION_ID')
        AZURE_TENANT_ID = credentials('AZURE_TENANT_ID')
    }

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

        stage('deploy') {
            environment {
                USERDATA_TENANT_ID = credentials('USERDATA_TENANT_ID')
                USERDATA_CLIENT_SECRET = credentials('USERDATA_CLIENT_SECRET')
                USERDATA_BOT_PASSWORD = credentials('USERDATA_BOT_PASSWORD')
            }

            steps {
                sh '[ ! -z "${USERDATA_TENANT_ID}" ] && echo "solution.teamsAppTenantId=${USERDATA_TENANT_ID}" >> .fx/default.userdata'
                sh '[ ! -z "${USERDATA_CLIENT_SECRET}" ] && echo "fx-resource-aad-app-for-teams.clientSecret=${USERDATA_CLIENT_SECRET}" >> .fx/default.userdata'
                sh '[ ! -z "${USERDATA_BOT_PASSWORD}" ] && echo "fx-resource-bot.botPassword=${USERDATA_BOT_PASSWORD}" >> .fx/default.userdata'
                sh 'npx teamsfx deploy'
            }
        }

        stage('package') {
            steps {
                sh 'npx teamsfx package'
                archiveArtifacts artifacts: 'appPackage/appPackage.zip'
            }
        }

        stage('publish') {
            steps {
                sh 'npx teamsfx publish'
            }
        }
    }
}