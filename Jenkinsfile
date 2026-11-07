
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
			bat '''
			chcp 65001 > nul
			set PYTHONUTF8=1
			"C:\\Users\\yoloy\\AppData\\Local\\Programs\\Python\\Python312\\python.exe" -m pipenv run pytest
			'''
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
			chcp 65001 > nul
			set PYTHONUTF8=1
			"C:\\Users\\yoloy\\AppData\\Local\\Programs\\Python\\Python312\\python.exe" -m pipenv install --dev pytest
			"C:\\Users\\yoloy\\AppData\\Local\\Programs\\Python\\Python312\\python.exe" -m pipenv update
			"C:\\Users\\yoloy\\AppData\\Local\\Programs\\Python\\Python312\\python.exe" -m pipenv graph
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
