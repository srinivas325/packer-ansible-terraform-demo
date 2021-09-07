pipeline {
    agent any
    parameters {
        string(name: 'project_name', defaultValue: 'Packer Pipeline', description: 'Jenkins Pipeline for terraform?')
    }
    environment {
       
        access_key = 'acces_key'
        secret_key = 'secret_key'
    }
    stages {
          stage('code checkout') {
               steps {
                    git branch: 'master', url: 'https://github.com/srinivas325/packer-ansible-terraform-demo.git'
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

