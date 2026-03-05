pipeline {
    agent any

    parameters {
        booleanParam(name: 'DEPLOY', description: 'Want to deploy to Production')
    }
    
    environment {
        CURRENT_ENV = 'prod'
    }

    stages {
        stage('CEHCKOUT_REPOA') {
            steps {
                checkout ([ $class: 'GitSCM',
                            branches: [[name: '*/main']], 
                            extensions: [], 
                            userRemoteConfigs: [[
                                credentialsId: 'shrividyanavalgund-ux', 
                                url: 'https://github.com/shrividyanavalgund-ux/jenkin_repo.git'
                            ]]
                        ])
               
                sh '''
                    echo GIT_BRANCH: $GIT_BRANCH
                    echo BRANCH_NAME: $BRANCH_NAME
                '''
            }
        }

        stage('STAGE1 When branch main') {
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/main'
                }
            }
            steps {
                echo "This is stage1 running"
                sh ''' 
                    pwd
                    ls -lrt
                    sleep 5
                '''
            }
        }

        stage('when environment') {
            when {
                environment name: 'CURRENT_ENV', value: 'prod'
            }
            steps {
                echo "This is FINAL running"
                sh '''
                    pwd
                    ls -lrt
                    sleep 5
                '''
            }
        }

        stage('when parameter') {
            when {
                expression { params.DEPLOY == true }
            }
            steps {
                echo "This is FINAL running"
                sh 'sleep 5'
            }
        }
    }
}