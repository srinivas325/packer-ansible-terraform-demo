pipeline {
    agent any
    parameters {
        string(name: 'project_name', defaultValue: 'Packer Pipeline', description: 'Jenkins Pipeline for terraform?')
    }
    environment {
        terraform_version = '0.11.11'
        packer_version = '1.4.3'
        access_key = 'input_your_access_key'
        secret_key = 'input_your_secret_key'
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
          stage('Deploy??') {
                steps {
                    script {
                       timeout(time: 2, unit: 'MINUTES') {
                          input(id: "Deploy Gate", message: "Want to Deploy ${params.project_name}?", ok: 'Deploy??')
                       }
                    }
                }
          }
         
         }
}

