pipeline {
    agent {label 'swarm'}
    stages {
        stage('Test') {
            steps {
                sh ./gradlew build --no-daemon 
            }
        }
    }
}
