pipeline {
    agent any

    environment {
        IMAGE = "mi-app"
    }

    stages {

        stage('Clonar repositorio') {
            steps {
                git 'https://github.com/SebtianS/Proyecto-DevOps'
            }
        }

        stage('Construir imagen Docker') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Desplegar aplicación') {
            steps {
                sh '''
                docker stop mi-app || true
                docker rm mi-app || true
                docker run -d -p 3000:3000 --name mi-app $IMAGE
                '''
            }
        }
    }
}
