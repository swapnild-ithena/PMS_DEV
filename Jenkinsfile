pipeline {
    agent any
    tools { nodejs "nodeJS" }

    stage('Chekout') {
            steps {
                git branch: 'main', credentialsId: 'df639a56-04b5-408d-b7ad-995f87f75ab6', url: 'https://github.com/Pradip-Ithena/PMS_DEV.git'
                echo 'Checkout Completed'
            }
        }
    stages {
        stage('NPM Install') {
            steps {
                sh 'npm install'
                sh 'npm install http-server'
            }
        }
        stage('Test') {
            steps {
                sh 'ng test'
            }
        }
        stage('Build') {
            steps {
                sh 'ng build --prod'
            }
        }
        stage('Deploy') {
            steps {
                sh 'ng serve --host 192.168.1.41 --port 8081'
            }
        }
    }
}