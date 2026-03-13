pipeline {
    agent any
    stages {
        stage('Checkout (Ingredientes)') {
            steps {
                echo 'Descargando la receta de BurgerCode...'
                checkout scm
            }
        }
        stage('Build (Cocinar)') {
            steps {
                echo 'Cocinando la imagen Docker...'
                sh 'docker build -t burgercode-app .'
            }
        }
        stage('Deploy (Entrega)') {
            steps {
                echo 'Desplegando en Producción...'
                sh 'docker rm -f burger-prod || true'
                sh 'docker run -d --name burger-prod -p 5001:5000 burgercode-app'
                echo '¡Hamburguesa servida en http://localhost:5001!'
            }
        }
        stage('Deploy (Entrega)') {
            steps {
                echo 'Desplegando en Producción...'
                sh 'docker rm -f burger-prod || true'
                sh 'docker run -d --name burger-prod -p 5000:5000 --network host burgercode-app'
                echo '¡Hamburguesa servida en http://localhost:5000!'
            }
        }
    }
}
