pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo 'build'
                script{
                        
                                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                                    sh ' echo hello'
                                }
                    
                }
            }
        }
        stage('deploy') {
            steps {
                echo 'deploy'
                script {
                         
                                withCredentials([string(credentialsId: 'openshift', variable: 'KUBECONFIG')]) {
                                    sh '''
                                        oc login --token=sha256~J_11a-2Wq26kQ5V-gdq1Ck180gitT3ixC9Ob5byKkiA --server=https://api.ocpuat.devopsconsulting.org:6443
 --insecure-skip-tls-verify
                                        oc project sample-app
                                        oc create deployment app --image=openshiftivolve --replicas=1 --kubeconfig ${KUBECONFIG} -n sample-app
    
                                    '''
                                }
                         
                    }
                }
          }
    }
}
