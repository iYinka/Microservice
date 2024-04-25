pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-ms', contextName: '', credentialsId: 'k8-token-id', namespace: 'webapps', serverUrl: 'https://122A214DC570619DF3B8035ED528B2DD.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-ms', contextName: '', credentialsId: 'k8-token-id', namespace: 'webapps', serverUrl: 'https://122A214DC570619DF3B8035ED528B2DD.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
