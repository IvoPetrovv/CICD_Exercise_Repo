pipeline{
    agent any
    envirment{
        NODE_VERSION = '18.x'
    } 

    tools{
        nodejs "${NODE_VERSIO}"
    }

    stages{
        stage('Checkout'){
            steps{
                Checkout scm 
            }
        }

        stage('install dependencies'){
            steps{
                script{
                    if(isUnix()){
                       sh 'npm install'     
                    }
                    else{
                        sh 'npm install'  
                    }
                }
            }
        }

        stage('Start aplication and run test'){
            steps{
                script{
                   sh 'npm start &'
                   sh 'wait-on http://localhost:8090'
                   sh 'npm test' 
                }
            }
        }

    }

    post{
        always{
            echo "CI pipline completed" 
        }
    }
}