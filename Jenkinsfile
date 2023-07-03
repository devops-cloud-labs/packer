pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                sh '''
                    curl -o packer.zip https://releases.hashicorp.com/packer/1.8.5/packer_1.8.5_linux_amd64.zip
                    unzip packer.zip
                    sudo mv packer /usr/local/bin/
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    packer init .
                    packer build .
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '*'
        }
    }
}
