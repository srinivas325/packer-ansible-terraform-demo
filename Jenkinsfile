pipeline {
    agent any
    parameters {
        string(name: 'project_name', defaultValue: 'Packer Pipeline', description: 'Jenkins Pipeline for terraform?')
    }
 
    stages {
          stage('code checkout') {
               steps {
                    git branch: 'master', url: 'https://github.com/srinivas325/packer-ansible-terraform-demo.git'
                    }
          }
          stage('Build AMI') {
                steps {
                    script {
                    withCredentials([[
    $class: 'AmazonWebServicesCredentialsBinding',
    credentialsId: "189e221c-239c-4e34-94b3-e846187366bf",
    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
]]) 
                    dir('./packer'){
                     sh 'ls -la; pwd; AWS_PROFILE=dev packer build template.json'
                    }
                }
          }
          }
         
         }
}

