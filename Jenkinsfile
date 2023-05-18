pipeline {
    agent any
    triggers { 
        pollSCM('*/1 * * * *') 
    }

    stages {
        stage('install-pip-deps') {
            steps {
                script {
                    build()
                }
            }
        }
        stage('deploy-to-dev') {
            steps {
                script {
                    deploy("dev", 7001)
                }
            }
        }
        // stage('tests-on-dev') {
        //     steps {
        //         script{
        //             test("BOOKS", "dev")
        //         }
        //     }
        // }
        stage('deploy-to-staging') {
            steps {
                script {
                    deploy("staging", 7002)
                }
            }
        }
        // stage('tests-on-staging') {
        //     steps {
        //         script{
        //             test("BOOKS", "staging")
        //         }
        //     }
        // }
        stage('deploy-to-preprod') {
            steps {
                script {
                    deploy("preprod", 7003)
                }
            }
        }
        // stage('tests-on-preprod') {
        //     steps {
        //         script{
        //             test("BOOKS", "preprod")
        //         }
        //     }
        // }
        stage('deploy-to-prod') {
            steps {
                script {
                    deploy("prod", 7004)
                }
            }
        }
        // stage('tests-on-prod') {
        //     steps {
        //         script{
        //             test("BOOKS", "prod")
        //         }
        //     }
        // }
        // stage('Delete all') {
        //     steps {
        //         script {
        //             deleteAll()
        //         }
        //     }
        // }
    }
}

def build() {
    echo "Building of node application is starting.."
    git branch: 'main', poll: false, url: 'https://github.com/OlegsBrown/python-greetings.git'
    bat "npm install pm2 -g"
    bat "dir"
    bat "pip3 install -r requirements.txt"
}

// def deleteAll() {
//     echo "Deleting all node is starting.."
//     git branch: 'main', poll: false, url: 'https://github.com/OlegsBrown/python-greetings.git'

// }

def deploy(String environment, int port) {
    echo "Deployment to ${environment} has started.."
    git branch: 'main', poll: false, url: 'https://github.com/OlegsBrown/python-greetings.git'
    bat 'npm install -g'
    bat "C:\\Users\\ole6k\\AppData\\Roaming\\npm\\pm2 delete \"books-${environment}\" & EXIT /B 0"    
    bat "C:\\Users\\ole6k\\AppData\\Roaming\\npm\\pm2 start app.py --name \"greetings-app-${environment}\" --env port=${port}"

}
