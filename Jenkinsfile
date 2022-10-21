pipeline{
    agent any

    //pipeline tools and their registered names in the agents
    tools{
        maven 'maven'
        git 'git'
    }

    //parameters
    parameters{
        string(name: 'repo', defaultValue: 'source1', description: 'build version')
        choice(name : 'VERSION', choices:['1.1.0','1.2.0'], description: '')
        booleanParam(name: 'allowTests', defaultValue:true, description:'')
    }

    //used to set Environment variables
    environment{
        CURRENT_VERSION='0.1'
        SERVER_CREDENTIALS=credentials('azure-key')
    }

    //stages of pipeline
    stages{
        stage('dev-build')
        {   
            //condintion for execution
            when{
                expression{
                    BRANCH_NAME=='dev'
                }
            }

            //excution node
            agent{
                label 'build-engine'
            }

            //steps
            steps{
                echo "building  verison ${CURRENT_VERSION}" //double quote is required for in-line variable call
                echo 'building version ${CURRENT_VERSION}' //everything is string
            }
        }
        stage('dev-test'){
            when{
                expression{
                    //how to use env variable and parameters
                    BRANCH_NAME=='dev' && param.allowTests==true
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
                //if credentials are needed
                withCredentials([
                    usernamePassword(credentials: 'azure-keys', username: "${USERNAME}", password: "${PASSWORD}")
                ])
                {

                }

            }
        }
    }

    //post build steps
    post{
        always{

        }
        success{

        }
        failure{

        }
    }
}