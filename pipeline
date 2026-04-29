pipeline {

    agent {
        kubernetes {

            cloud 'kubernetes'

            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: jnlp
    image: jenkins/inbound-agent:latest
    tty: true
'''
        }
    }

    stages {

        stage('Verify Agent') {

            steps {

                sh 'echo "Executor Hostname:"'
                sh 'hostname'

                sh 'echo "Running User:"'
                sh 'whoami'
            }
        }
    }
}
