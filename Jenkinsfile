pipeline {
    agent {
        kubernetes {
            cloud 'kubernetes'
            inheritFrom 'jenkins-agent'
        }
    }

    options {
        skipDefaultCheckout(true)
    }

    stages {

        stage('Executor Attachment proof') {
            steps {
                sh '''
                echo "Executor attached"
                hostname
                whoami
                '''
            }
        }

        stage('Cluster Info') {
            steps {
                sh '''
                echo "Fetching cluster info..."
                kubectl cluster-info
                kubectl get nodes
                kubectl get pods -A
                '''
            }
        }
    }
}
