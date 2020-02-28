pipeline {
    environment {
        registry = "artrojort/act4image"
        registryCredential = 'docker'
    }
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
            steps {
                sh './gradlew build --no-daemon'
            }
        }
        stage('Building image') {
            steps{
                script {
                    docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
    }
}
