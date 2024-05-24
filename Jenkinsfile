pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'cluster-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'cluster-1-dns-ekjzuhwp.hcp.eastus.azmk8s.io']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'cluster-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'cluster-1-dns-ekjzuhwp.hcp.eastus.azmk8s.io']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
