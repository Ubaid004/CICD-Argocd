pipeline{
    agent any

    environment{
        Dockerhun_Usrname= "ubaid004"
        Credentials= "dockerhubid"
    }
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
                    docker.withRegistry('', Credentialse) {
                        sh '''
                        docker tag cicd-argocd ubaid004/cicd-argocd:cicd-argocd
                        docker push ubaid004/cicd-argocd:cicd-argocd
                        '''
                    }

                }
            }
        }
    }
}
