
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compilando / preparando entorno...'
            }
        }

        stage('Test') {
            steps {
                bat 'pipenv run pytest'
            }
        }

        stage('Analyze') {
            steps {
                echo 'Análisis de calidad de código (puede integrarse con SonarQube aquí)'
            }
        }

        stage('Dependency Management') {
            steps {
                bat '''
                    pipenv install
                    pipenv update
                    pipenv graph
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando aplicación en entorno de prueba (simulado)...'
            }
        }
    }
}
