pipeline{
    agent any
    

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

        stage('Start aplication'){
            steps{
                script{
                   bat 'start /b npm start'
                 }
            }
        }
        stage('Run test'){
            steps{
                script{
                   bat 'start npm test' 
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