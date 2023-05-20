pipeline {
    agent any
    triggers{ pollSCM('*/1 * * * *') }
    
    stages {
        stage('Build') {
            steps {
                script{
                    build()
                }
            }
        }
        stage('Install pip deps') {
            steps {
                script{
                    deps()
                }
            }
        }
        stage('Deploy to DEV') {
            steps {
                script{
                    deploy("DEV")
                }
            }
        }
    }
}

def build(){
    echo "Building of node application is starting, installing all required dependencies.."
    //bat "npm install"
    bat "npm install -g pm2"
    bat "npm install --save-dev mocha"

}

def deps(){
    echo "Installing pip deps"
    bat "npm install"
    bat "dir"
    //bat "npm test"
}

def deploy(String environment){ 
    echo "Deployment to ${environment} has started.."
    bat "C:\\Users\\Samanta\\AppData\\Roaming\\npm\\pm2 delete \"books-${environment}\" & EXIT /B 0"
   // bat "C:\\Users\\Samanta\\AppData\\Roaming\\npm\\pm2 start -n \"books-${environment}\" index.js -- 7001"
}