Pipeline {
    
    stages {
        stage('build') {
            steps {
                echo 'build'
                script{
                        
                                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                                    sh '''
                                        docker login -u ${USERNAME} -p ${PASSWORD}
                                        docker build -t abdo23/openshiftivolve:v1 .
                                        docker push abdo23/openshiftivolve:v1
                                        
                                    '''
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

                                        oc create deployment app --image=openshiftivolve --replicas=1 --kubeconfig ${KUBECONFIG} -n jenkins
    
                                    '''
                                }
                         
                    }
                }
          }
    }
}
