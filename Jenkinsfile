pipeline {
    agent {label 'ansible'}
    stages {
        stage('Check Versions'){
            steps {
                sh '''
                    kubectl version
                '''
            }
        }

        stage('List Pods') {
            steps {
                sh '''
                    kubectl get pods -A
                '''
            }
        }
    }
}