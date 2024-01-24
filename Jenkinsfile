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
                         
                                withCredentials([file(credentialsId: '	openshift-credentials', variable: 'KUBECONFIG')]) {
                                    sh '''

                                        oc create deployment app --image=openshiftivolve --replicas=1 --kubeconfig ${KUBECONFIG} -n abdelrahman
    
                                    '''
                                }
                         
                    }
                }
          }
    }
}
