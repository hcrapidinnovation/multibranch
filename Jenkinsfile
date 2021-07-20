properties([pipelineTriggers([githubPush()])])
pipeline{
    agent any
    stages{
        stage('checkou'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/devadikhagesh/multibranch.git']]])
            }
        }
    }
}
