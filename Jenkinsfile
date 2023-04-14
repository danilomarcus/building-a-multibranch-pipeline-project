pipeline {
    agent {
        docker {
            image 'node:19-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver for Development') {
            when {
                branch 'development'
            }
            steps {
                sh './jenkins/scripts/deliver-for-development.sh'
                input 'Deploy para ambiente de desenvolvimento?'
                sh './jenkins/scripts/kill.sh'
            }
        }
        stage('Deliver for Production') {
            when {
                branch 'production'
            }
            steps {
                sh './jenkins/scripts/deliver-for-production.sh'
                input 'Deploy para ambiente de Produção?'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
