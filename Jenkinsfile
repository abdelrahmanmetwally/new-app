pipeline {
    agent any


   
    stages {
        stage('build') {
            steps {
                echo 'build'
                script{
                        
                                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                                    sh ' echo hello'
                                    sh ' docker login -u ${USERNAME} -p ${PASSWORD} '
                                    sh ' docker build -t abdo23/new-project-app:v${BUILD_NUMBER} . '
                                    sh ' docker push abdo23/new-project-app:v${BUILD_NUMBER} '
                                }
                    
                }
            }
        }
        stage('deploy') {
            steps {
                echo 'deploy'
                script {
                    sh ' echo hello'
                         
                                // withCredentials([file(credentialsId: 'openshift-credentials', variable: 'KUBECONFIG')]) {
                                //     sh '''
                                //         oc login --token=${login} --server=https://api.ocpuat.devopsconsulting.org:6443  --insecure-skip-tls-verify
                                //         oc project sample-app
                                //         oc create deployment app --image=openshiftivolve --replicas=1 --kubeconfig ${KUBECONFIG} -n sample-app
    
                                //     '''
                                // }
                         
                    }
                }
          }
    }
}
