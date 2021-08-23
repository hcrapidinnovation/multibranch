properties([pipelineTriggers([githubPush()])])
pipeline {
agent any
    parameters {
        string(name: 'delete_container', defaultValue: 'BUST-referral-backend-app')
        string(name: 'delete_image', defaultValue: 'BUST-referral-image')
        string(name: 'branch', defaultValue: 'prod')
        credentials(name: 'gitcredentials',type: 'Username with password' defaultValue: 'gitcredentials')
    }
    stages {
        stage('Code Checkout'){
             agent {label 'master'}
            steps{
                echo "code checkout from main branch"

                git ( url: 'https://github.com/devadikhagesh/multibranch.git/' ,credentialsId: "${gitcredentials}", branch: "${branch}")
            }
        }
     stage('Clear image and container'){
          agent {label 'master'}
          steps{
                sh '''
                    echo "container and image remove"
                    sudo docker stop ${delete_container}
                    sudo docker rm ${delete_container}
                    sudo docker rmi ${delete_image}
                ''' 
            }
        }
        stage('Run Docker container'){
             agent {label 'master'}
            steps{
                sh '''
                    echo "Container Running"
                    ls
                    sudo docker run --name ${delete_container} -d -p 3000:3000 ${delete_image}
                    echo "Finished"
                '''
            }
        }
    }
}
