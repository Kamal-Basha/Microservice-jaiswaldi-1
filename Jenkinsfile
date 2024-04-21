pipeline {
    agent any

    stages {
        stage('deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-jai-1', contextName: '', credentialsId: 'k8-token', namespace: '', serverUrl: 'https://8EE899DE13C35FCC694483760727A13C.gr7.ap-south-1.eks.amazonaws.com']]) {
                  
                    sh  "kubectl apply -f deployment-adservice.yml"

                }
            }
        }
        
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-jai-1', contextName: '', credentialsId: 'k8-token', namespace: '', serverUrl: 'https://8EE899DE13C35FCC694483760727A13C.gr7.ap-south-1.eks.amazonaws.com']]) {
                     sh "kubectl get svc -n webapps"
                }
            }
        }
        
    }
}
