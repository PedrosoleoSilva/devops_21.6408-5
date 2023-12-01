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

    options {
        // Defina as opções do pipeline, se necessário
        skipStagesAfterUnstable()
    }

    environment {
        // Defina as variáveis de ambiente necessárias
        NODEJS_HOME = tool name: 'node_modules', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
    }

    stages {
        stage('Declarative: Checkout SCM') {
            steps {
                // Se necessário, adicione mais passos nesta etapa
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Adicione comandos para a construção da aplicação
                sh 'npm install'
            }
        }

        // Adicione mais estágios conforme necessário para testes, deploy, etc.
    }

    post {
        success {
            // Adicione ações a serem executadas em caso de sucesso (opcional)
            echo 'Pipeline executada com sucesso!'
        }
        failure {
            // Adicione ações a serem executadas em caso de falha (opcional)
            echo 'Pipeline falhou!'
        }
    }
}
