pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Nestel2022/obsschool_devops_webserver'
            }
        }
        stage('Configurar archivo') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'Credentials_DevOps',
                                                 usernameVariable: 'USER',
                                                 passwordVariable: 'PASS')]) {
                    sh '''
                        echo "[credentials]" > credentials.ini
                        echo "user=${USER}" >> credentials.ini
                        echo "password=${PASS}" >> credentials.ini
                    '''
                    archiveArtifacts artifacts: 'credentials.ini', fingerprint: true
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
