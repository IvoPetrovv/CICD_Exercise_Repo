pipeline{
    agent any
    envirment{
        NODE_VERSION = '18.x'
    } 

    tools{
        nodejs "${NODE_VERSION}"
    }

    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/IvoPetrovv/CICD_Exercise_Repo'
            }
        }

        stage('install dependencies'){
            steps{
                script{
                    if(isUnix()){
                       bat 'npm install'     
                    }
                    else{
                        bat 'npm install'  
                    }
                }
            }
        }

        stage('Start aplication and run test'){
            steps{
                script{
                   bat 'npm start &'
                   bat 'wait-on http://localhost:8090'
                   bat 'npm test' 
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