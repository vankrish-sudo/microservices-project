pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9DAEBCA4E7C309F5A59C6738246BE29F.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9DAEBCA4E7C309F5A59C6738246BE29F.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
