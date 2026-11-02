pipeline {
    agent any

    stages {
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner'

                    withSonarQubeEnv('SonarQube-Server') {
                        bat "\"${scannerHome}\\bin\\sonar-scanner.bat\" -Dsonar.projectKey=flaskkidk -Dsonar.sources=."
                    }
                }
            }
        }
    }
}
