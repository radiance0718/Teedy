pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                h 'mvn -B -DskipTests clean package'
            }
        }
        stage('K8s') {
            steps {
                sh 'kubectl set image vv381/teedy container-name=teedy'
            }
        }
    }
}
