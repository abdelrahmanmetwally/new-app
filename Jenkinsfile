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
                                        oc login -u abdelrahman -p abdelrahman console-openshift-console.apps.ocpuat.devopsconsulting.org/ --insecure-skip-tls-verify
                                        oc create deployment app --image=openshiftivolve --replicas=1 --kubeconfig ${KUBECONFIG} -n sample-app
    
                                    '''
                                }
                         
                    }
                }
          }
    }
}
