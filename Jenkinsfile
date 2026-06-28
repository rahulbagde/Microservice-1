pipeline {
    agent any

    stages {
        stage('Deploy to K8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'production-eks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F54EC392F01B23C2AA57FD319522DC2F.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'production-eks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F54EC392F01B23C2AA57FD319522DC2F.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
