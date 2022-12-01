pipeline {
    agent any

    stages {
        stage('Sonar checking') {
            steps {
                sh '''/opt/sonar-scanner/bin/sonar-scanner \\
                  -Dsonar.projectKey=AppJenkins \\
                  -Dsonar.sources=. \\
                  -Dsonar.host.url=http://172.17.0.3:9000 \\
                  -Dsonar.login=sqp_3285e07cf70a0e1e14e5c1fa7f7744eb872f288e'''
            }
        }
       
        stage('PHP deploy app') {
            steps {
                
                sshPublisher(publishers: [sshPublisherDesc(configName: 'MyWebsite', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.php')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
               
            }
        }

        stage('notify') {
            steps {
                 slackSend channel: '#integracion-continua', message: "test de despliegue de app desde github ${env.JOB_NAME} "
            }
        }
    }
}
