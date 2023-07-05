pipeline {
  agent any

  environment {
    AWS_ACCESSKEY = credentials('AWS_SECRET_KEY_ID')
    AWS_SECRETKEY = credentials('AWS_SECRET_ACCESS_KEY')
  }

  stages {
    stage('Pull Code from GitHub') {
      steps {
        git branch: 'main', url: 'https://github.com/nabeeljb/packer.git'
      }
    }

    stage('Create and Publish AMI') {
      steps {
        script {
          env.AWS_ACCESS_KEY_ID = "${AWS_ACCESSKEY}"
          env.AWS_SECRET_ACCESS_KEY = "${AWS_SECRETKEY}"
          sh "packer init Part1/aws-ubuntu.pkr.hcl"
          sh "packer build Part1/aws-ubuntu.pkr.hcl"
        }
      }
    }
  }
}
