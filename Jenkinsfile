pipeline {
    agent {
        kubernetes {
            cloud 'kubernetes'
            defaultContainer 'kubectl'   // 👈 IMPORTANT FIX
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: jnlp
    image: jenkins/inbound-agent
    args: ['$(JENKINS_SECRET)', '$(JENKINS_NAME)']
  - name: kubectl
    image: bitnami/kubectl:1.30.1-debian-12-r0
    command:
    - cat
    tty: true
'''
        }
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
