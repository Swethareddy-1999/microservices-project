pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'swetha', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B83D8B320AEAD7F7D0CA75F6E5A4AE67.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'swetha', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B83D8B320AEAD7F7D0CA75F6E5A4AE67.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
