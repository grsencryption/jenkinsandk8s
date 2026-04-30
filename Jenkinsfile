pipeline {
    agent {
        kubernetes {
            cloud 'kubernetes'
            inheritFrom 'jenkins-agent'
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: kubectl
    image: bitnami/kubectl:latest
    command:
    - cat
    tty: true
'''
        }
    }

    options {
        skipDefaultCheckout(true)
    }

    stages {

        stage('Executor Attachment proof') {
            steps {
                container('kubectl') {
                    sh '''
                    echo "Executor attached"
                    hostname
                    whoami
                    '''
                }
            }
        }

        stage('Cluster Info') {
            steps {
                container('kubectl') {
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
}
