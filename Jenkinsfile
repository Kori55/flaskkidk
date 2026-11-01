pipeline {
    agent any

    stages {
        stage('Dependency Check') {
            steps {
                bat 'if not exist reports mkdir reports'

                dependencyCheck(
                    odcInstallation: 'Dependency-Check',
                    additionalArguments: '--scan . --format HTML --format XML --out reports'
                )
            }

            post {
                always {
                    dependencyCheckPublisher(
                        pattern: 'reports/dependency-check-report.xml'
                    )
                }
            }
        }
    }
}