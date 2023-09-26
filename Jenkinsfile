pipeline {
  agent {
    label 'ansible-server'
  }
  stages {
    stage('deploy patch1 playbook'){
      steps{
        dir('/home/ec2-user/ansible-dev'){
          sh 'ansible-playbook patch1.yml'
        }
      }
    }
    
  }
}
