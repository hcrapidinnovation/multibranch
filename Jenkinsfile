pipeline{
    agent any
    stages{
        stage('checkout git'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/prod']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/devadikhagesh/multibranch.git']]])
            }
        }
    }
}
