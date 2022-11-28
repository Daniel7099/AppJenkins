pipeline {
    agent any

    stages {
        stage('Sonar checking') {
            steps {
                sh '''sonar-scanner \\
                  -Dsonar.projectKey=AppJenkins \\
                  -Dsonar.sources=. \\
                  -Dsonar.host.url=http://localhost:9000 \\
                  -Dsonar.login=sqp_3285e07cf70a0e1e14e5c1fa7f7744eb872f288e'''
            }
        }
    }
}
