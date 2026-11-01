pipeline {
    agent any

    stages {
        stage('Dependency Check') {
            steps {
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