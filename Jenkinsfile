pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'E-commerce-EKS', contextName: '', credentialsId: 'k8-token-id', namespace: 'webapps', serverUrl: 'https://02206FAA5BF7A54130262DD3FB66CC17.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'E-commerce-EKS', contextName: '', credentialsId: 'k8-token-id', namespace: 'webapps', serverUrl: 'https://02206FAA5BF7A54130262DD3FB66CC17.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
