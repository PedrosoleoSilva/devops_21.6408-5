pipeline{
    agent any

    stages {
        stage('Build'){
            steps {
                sh  '''
                java --version
                docker version
                docker-compose version
                '''
            }
        }
    }
    
}
pipeline {
    agent any

    stages {
        stage('Testes de Segurança') {
            steps {
                script {
                    // Inicialize a aplicação
                    sh 'npm install'

                    // Execute os testes
                    sh 'npm test'
                }
            }
        }
        // Adicione mais estágios conforme necessário para construção, deploy, etc.
    }

    post {
        success {
            echo 'Pipeline executada com sucesso!'
        }
        failure {
            echo 'Pipeline falhou!'
        }
    }
}
