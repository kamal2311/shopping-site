pipeline {
    agent { docker { image 'node:12.0' } }
    stages {
        stage('Build') {
            steps {
                sh 'npm --version'
                sh 'echo "Hello World"'
                sh '''
                    npm install
                    npm run build:ci
                '''
            }
        }
        stage('Test') {
            steps {                                
                sh 'npm install && npm run test:ci'                                    
            }
        }
        stage('Deploy') {
            environment {
                SURGE_DOMAIN = credentials('SURGE_DOMAIN')
                SURGE_TOKEN = credentials('SURGE_TOKEN')
            }
            steps {                                
                sh 'npx surge --project=./dist/shopping-site/ --domain=$SURGE_DOMAIN --token=$SURGE_TOKEN'
            }
        }

    }
}