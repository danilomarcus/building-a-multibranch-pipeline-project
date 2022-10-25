pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000 -p 50000:50000'
        }
    }
    enviroment {
        CI = true
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
    }
}
