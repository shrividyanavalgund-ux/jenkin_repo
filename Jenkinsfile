pipeline{
    agent {label 'slave1'}
    stages{
        stage('build1'){
            steps{
                echo "build1"
            }
        }
        stage('build2'){
            steps{
                echo "build2"
                sh '''
                pwd
                '''
            }
        }
    }
}