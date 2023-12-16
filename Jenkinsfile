pipeline {
    agent {label 'MAVEN'}
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 30, unit: 'MINUTES')
    triggers {
        pollSCM('* * * * *')
      }
    }
    stages {
        stage('git') {
            steps {
                git url: 'https://github.com/Maheshp70/taxi-booking.git',
                branch: 'main'
            }
        }
        stage('build') {
          steps {
            sh 'mvn clean package'
          }
        }
    }
}