pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Nestel2022/obsschool_devops_webserver'
            }
        }
       stage('Pruebas de SAST y Env') {
            parallel {
                stage('Pruebas de SAST') {
                    steps {
                        echo 'Ejecución de pruebas de SAST'
                    }
                }
                stage('Imprimir Env') {
                    steps {
                        echo "WORKSPACE path: ${env.WORKSPACE}"
                    }
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
