pipeline {
agent any
stages {
stage('Provision infrastructure') {
 steps {
   sh 'D:\Shashank\terraform init'
   sh 'D:\Shashank\terraform plan -out=plan'

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
        
          sh '/usr/local/bin/terraform apply plan'
        
      }
    }
}
}
 
