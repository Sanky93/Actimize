pipeline {
agent any
stages {

stage('Set Terraform path') {
 steps {
 script {
 def tfHome = tool name: 'Terraform'
 env.PATH = “${tfHome}:${env.PATH}”
 }
 }
}

stage('Provision infrastructure') {
 steps {
   bat label: '', script: 'terraform init'
  bat label: '', script: 'terraform plan -out=plan'

 }
}
  stage('Approval') {
      steps {
        script {
          def userInput = input(id: 'confirm', message: 'Apply Terraform?', parameters: [ [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Apply terraform', name: 'confirm'] ])
        }
      }
    }
stage('TF Apply') {
      steps {
        
          bat label: '', script: 'terraform apply plan'
        
      }
    }
}
}