# teste_jenkins

pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }

    stages {
        stage('gitclone') {
            steps {
                git branch: 'main', url: 'https://github.com/cibellemc/teste_jenkins'
            }
        }
    }

    post {
        success {
            echo 'Deploy realizado com sucesso!'
        }
        failure {
            echo 'Falha no deploy.'
        }
    }
}
