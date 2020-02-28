pipeline {
    agent none 
    stages {
        stage('build') {
            agent {
                dockerfile {
                    filename 'Dockerfile.slave'
                    additionalBuildArgs '--build-arg version=1.0.2'
                    args '-v /tmp:/tmp'
                }
            }  
            environment {
                registry = "artrojort/act4image"
                registryCredential = 'docker'
            }
            steps {
                sh './gradlew build --no-daemon'
                docker.build registry + ":$BUILD_NUMBER"
            }
        }
    }
}
