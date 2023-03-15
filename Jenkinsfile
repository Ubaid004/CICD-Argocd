pipeline{
    agent any
    stages{
        stage("Checkout SCM"){
            steps{
                git url: "https://github.com/Ubaid004/CICD-Argocd.git" ,branch: 'dev'
            }
        }
        stage("build"){
            steps{
                script {
                sh 'docker build . -t cicd-argocd'
                }
            }
        }
        stage("push"){
            steps{
                script {
                    withCredentials([usernameColonPassword(credentialsId: 'dockerhubid', variable: 'dockerhubCredentials')]) {
                        sh '''
                        docker login -u ubaid004 -p {dockerhubCredentials}
                        docker tag cicd-argocd ubaid004/cicd-argocd:cicd-argocd
                        docker push ubaid004/cicd-argocd:cicd-argocd
                        '''
                    }

                }
            }
        }
    }
}