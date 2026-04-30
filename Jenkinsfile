pipeline{
    agent{
        kubernetes{
            cloud 'kubernetes'
            inheritFrom 'jenkins-agent'
        }
    }

    options{
        skipDefaultCheckout(true)
    }

    stages{

        stage('Executor Attachment proof'){
            steps{
                sh '''
                echo "Executor attached"
                hostname
                whoami
                '''
            }
        }
        stage('Cluster Info'){
            steps{
                sh '''
                echo "Cluster Info"
                kubectl cluster-info
                '''
            }
        }
    }
}
