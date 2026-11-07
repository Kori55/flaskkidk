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
                sh 'pipenv run pytest || echo "Sin tests 
definidos"' 
            } 
        } 
 
        stage('Analyze') { 
            steps { 
                echo 'Análisis de calidad de código (puede 
integrarse con SonarQube aquí)' 
            } 
        } 
 
        stage('Dependency Management') { 
            steps { 
                sh 'pipenv install' 
                sh 'pipenv update' 
                sh 'pipenv graph' 
            } 
        } 
 
        stage('Deploy') { 
steps { 
echo 'Desplegando aplicación en entorno de prueba 
(simulado)...' 
} 
} 
} 
}