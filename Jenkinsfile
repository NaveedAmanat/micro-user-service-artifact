pipeline{
    agent any
    stages{
        stage('Push Manifest'){
            steps{
                script{
                    withCredentials([usernamePassword(credentialsId: 'Github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh "git config user.email mnaveed0004@gmail.com"
                        sh "git config user.name NaveedAmanat"
                        sh "sed -i 's+naveed0004/user-service.*+naveed0004/user-service:${IMAGE_TAG}+g' devolpment/deployment.yml"
                        sh "cat devolpment/deployment.yml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job update artifact:v${IMAGE_TAG}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/micro-user-service-artifact.git HEAD:main"
                    }
                }
            }
        }
    }
}
