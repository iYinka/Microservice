pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myEKS', contextName: '', credentialsId: 'k8-token-id', namespace: 'webapps', serverUrl: 'https://AA773E0DB4626BD6BCD389D178E57B1A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myEKS', contextName: '', credentialsId: 'k8-token-id', namespace: 'webapps', serverUrl: 'https://AA773E0DB4626BD6BCD389D178E57B1A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
