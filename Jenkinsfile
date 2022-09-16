pipeline {
  agent any
  tools {
    nodejs "nodeJS"
  }
  stages {
    stage('Chekout') {
      steps {
        git branch: 'main', credentialsId: '9cc6dcda-ec9f-4b57-939b-9985d0298570', url: 'https://github.com/Pradip-Ithena/PMS_DEV.git'
        echo 'Checkout Completed'
      }
    }
    stage('NPM Install') {
      steps {
        bat 'npm install'
        bat 'npm install http-server'
        echo 'installation Completed'
      }
    }
    stage('Test') {
      steps {
        echo 'test Completed'
      }
    }
    stage('Build + SonarQube analysis') {
      steps {
        withSonarQubeEnv('sonar', envOnly: true) {
          println $ {
            env.SONAR_HOST_URL
          }
        }
        bat 'npm run ng build'
        echo 'build Completed'
      }
    }
    stage('Deploy') {
      steps {
        bat 'npm run ng serve --host 65.2.163.29 --port 4201'
      }
    }
  }
}
