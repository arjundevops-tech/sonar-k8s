pipeline {
  agent any 
   stages {
     stage ('eks authentication'){
       steps {
         script {
            withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'eks-credentials']]) {
                  sh """
                        export AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID
                        export AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY
                        export AWS_DEFAULT_REGION=us-east-2
                        aws eks update-kubeconfig --region us-east-2 --name staging-demo
                        kubeclt get nodes
                    """
            }
         }
       }
     }
   }
}