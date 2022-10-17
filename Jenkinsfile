pipeline{
    agent any

    environment{
        CURRENT_VERISON='0.1'
    }

    stages{
        stage('dev-build')
        {
            when{
                expression{
                    BRANCH_NAME=='dev'
                }
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