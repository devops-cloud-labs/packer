pipeline {
  agent any
  environment {
    AWS_ACCESSOBJ = credentials('AWS_SECRET_KEY_ID')
    AWS_SECRETOBJ = credentials('AWS_SECRET_ACCESS_KEY')
  }
  stages {
    stage('Create and Publish AMI') {
      steps {
        script {
          env.AWS_ACCESS_KEY_ID = "${AWS_ACCESSOBJ_PSW}"
          env.AWS_SECRET_ACCESS_KEY = "${AWS_SECRETOBJ_PSW}"
          sh "packer init Part1/aws-ubuntu.pkr.hcl"
          sh "packer build Part1/aws-ubuntu.pkr.hcl"
        }
      }
    }
  }
}

