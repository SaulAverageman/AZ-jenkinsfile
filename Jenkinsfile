pipeline{
    agent any

    tools{
        maven
        git
    }

    environment{
        CURRENT_VERSION='0.1'
        SERVER_CREDENTIALS=credentials('azure-key')
    }

    stages{
        stage('dev-build')
        {
            when{
                expression{
                    BRANCH_NAME=='dev'
                }
            }

            agent{
                label 'build-engine'
            }

            steps{
                echo "building  verison ${CURRENT_VERSION}" //double quote is required for in-line variable call
                echo 'building version ${CURRENT_VERSION}' //everything is string
            }
        }
        stage('dev-test'){
            when{
                expression{
                    BRANCH_NAME=='dev'
                }
            }
            steps{

            }
        }


        stage('prod-build'){
            when{
                expression{
                    BRANCH_NAME=='prod'
                }
            }

            agent{
                label 'build-engine'
            }

            steps{

            }
        }
        stage('prod-test'){
            when{
                expression{
                    BRANCH_NAME=='prod'
                }
            }

            steps{
                withCredentials([
                    usernamePassword(credentials: 'azure-keys', username: "${USERNAME}", password: "${PASSWORD}")
                ])
                {

                }

            }
        }
    }
    post{
        always{

        }
        success{

        }
        failure{

        }
    }
}