pipeline {
    agent { docker { image 'node:12.0' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
            }
        }
    }
}