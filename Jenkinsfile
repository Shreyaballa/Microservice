pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://1DC7EBCE717008E4E0D8A30B7AA43106.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                     sh "kubectl apply -f deployment-service.yml"
                     sleep 60
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://1DC7EBCE717008E4E0D8A30B7AA43106.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                     sh "kubectl get deployments -n webapps"
                }
            }
        }   
    }
}
