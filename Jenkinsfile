pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Nestel2022/obsschool_devops_webserver'
            }
        }
        stage('Pruebas de SAST') {
            steps {
                withSonarQubeEnv('SonarQubeServer') {
                    sh 'sonar-scanner'
                }
            }
        }
        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: false
                }
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t devops_ws .'
            }
        }
    }
}
