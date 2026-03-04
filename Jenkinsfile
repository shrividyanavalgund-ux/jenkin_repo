pipeline {
    agent none

    parameters {
        string(name: 'NAME', defaultValue: '', description: 'Please tell me you name?')
        booleanParam(name: 'SKIP_TEST', description: 'Want to skip test runs to direct deploy')
        choice(name: 'BRANCH', choices: ['master','stagging','prod'], description: '')
    }
    
    stages {
        stage('STAGE1') {
            
            agent { label 'slave1' }

            steps {
               echo "NAME: ${params.NAME}"
               echo "SKIP_TEST: ${params.SKIP_TEST}"
               echo "BRANCH TO DEPLOY: ${params.BRANCH}"

               sh '''pipeline {
    agent any

    environment {
       DOCKER_USER = 'jaintpharsha'
       AWS_ACCESS_KEY = '65197561895639156'
    }

    stages {
        stage('STAGE1') {
            environment {
                STAGE = 'stage1'
            }
                
            steps {
                echo "DOCKER_USER: ${env.DOCKER_USER}"
                echo "AWS_ACCESS_KEY: ${env.AWS_ACCESS_KEY}"
                echo "STAGE: ${env.STAGE}"
            sh '''
                env
            '''
            }
        }
        
         stage('STAGE2') {
            steps {
               echo "DOCKER_USER: ${env.DOCKER_USER}"
               echo "AWS_ACCESS_KEY: ${env.AWS_ACCESS_KEY}"
               echo "STAGE: ${env.STAGE}"
               sh '''
                   env
               '''
            }
        }
    }
}
                    echo "NAME: ${NAME}"
                    echo "SKIP_TEST: ${SKIP_TEST}"
                    echo "BRANCH TO DEPLOY: ${BRANCH}"
               '''
            }
        }
        
    }
}