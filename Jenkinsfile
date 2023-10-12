pipeline {
    agent {
        docker {
            image 'node:18.18.0-alpine3.18' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Deliver') {
            steps {
                sh './Jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './Jenkins/scripts/kill.sh'
            }
        }
    }
}