pipeline {
    agent { label 'MAVEN' }
    options { 
        timeout(time: 20, unit: 'MINUTES') 
    }
    triggers {
        pollSCM('* * * * *')
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
            post {
                success {
                    archiveArtifacts artifacts: '**/taxi-booking-*.war'
                    junit testResults: '**/TEST-*.xml'
                }
            }
        }
    }

} 
