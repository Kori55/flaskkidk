
pipeline {
    agent any

    stages {
        stage('Dependency Check') {
            steps {
                catchError(buildResult: 'UNSTABLE', stageResult: 'FAILURE') {
                    bat 'if not exist reports mkdir reports'

                    dependencyCheck(
                        odcInstallation: 'Dependency-Check',
                        additionalArguments: '--scan . --format HTML --format XML --out reports'
                    )
                }
            }

            post {
                always {
                    dependencyCheckPublisher(
                        pattern: 'reports/dependency-check-report.xml'
                    )
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner'

                    withSonarQubeEnv('SonarQube-Server') {
                        bat """
                            "${scannerHome}\\bin\\sonar-scanner.bat" ^
                            -Dsonar.projectKey=flaskkidk ^
                            -Dsonar.projectName=flaskkidk ^
                            -Dsonar.sources=. ^
                            -Dsonar.exclusions=**/reports/**
                        """
                    }
                }
            }
        }

	stage('Deploy Flask') {
		steps {
			bat '''
				docker rm -f flask-app 2>NUL
            			docker run -d --name flask-app ^
                		-p 5000:5000 ^
                		-v "%CD%:/app" ^
                		-w /app ^
                		python:3.12-slim ^
                		sh -c "pip install -r requirements.txt && python t.py"
		        '''
			}
		}
	}
}
