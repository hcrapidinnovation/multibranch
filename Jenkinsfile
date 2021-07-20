pipeline{
    agent any
    stages{
        stage{
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/devadikhagesh/multibranch.git']]])
            }
        }
    }
}
