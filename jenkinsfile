pipeline {
  agent any
  
  stages {
    stage('Checkout') {
      steps {
        // Checkout the repository
        checkout scm
      }
    }
    
    stage('Build') {
      steps {
        // Install Packer
        sh 'curl -o packer.zip https://releases.hashicorp.com/packer/1.8.5/packer_1.8.5_linux_amd64.zip'
        sh 'unzip packer.zip'
        sh 'sudo mv packer /usr/local/bin/'
        
        // Execute build commands
        sh 'packer init .'
        sh 'packer build .'
      }
    }
  }
  
  post {
    success {
      // Archive build artifacts
      archiveArtifacts artifacts: '*'
    }
  }
}
