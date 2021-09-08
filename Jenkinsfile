//comments
pipeline {
    agent any
    parameters {
        string(name: 'project_name', defaultValue: 'Packer Pipeline', description: 'Jenkins Pipeline for terraform?')
    }
 environment {
    AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY')
    AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_KEY')
   
  }
    stages {
          stage('code checkout') {
               steps {
                    git branch: 'feature/packer-ansible', url: 'https://github.com/srinivas325/packer-ansible-terraform-demo.git'
                    }
          }
          stage('Build AMI') {
                steps {
                  
                    dir('./packer'){
                     sh 'ls -la; pwd; packer build template.json'
                    }
                }
          }
          }
         
         }

