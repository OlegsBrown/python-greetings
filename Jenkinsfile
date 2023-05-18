pipeline {
    agent any
    triggers{ pollSCM('*/1 * * * *') }
    

    stages {
        stage('install-pip-deps') {
            steps {
                script{
                    build()
                }
            }
        }
        // stage('deploy-to-dev') {
        //     steps {
        //         script{
        //             deploy("DEV", 1010)
        //         }
        //     }
        // }
        // stage('tests-on-dev') {
        //     steps {
        //         script{
        //             test("BOOKS", "DEV")
        //         }
        //     }
        // }
        // stage('deploy-to-staging') {
        //     steps {
        //         script{
        //             deploy("STG", 2020)
        //         }
        //     }
        // }
        // stage('tests-on-staging') {
        //     steps {
        //         script{
        //             test("BOOKS", "STG")
        //         }
        //     }
        // }
        // stage('deploy-to-preprod') {
        //     steps {
        //         script{
        //             deploy("PRD", 3030)
        //         }
        //     }
        // }
        // stage('tests-on-preprod') {
        //     steps {
        //         script{
        //             test("BOOKS", "PRD")
        //         }
        //     }
        // }
        //         stage('deploy-to-prod') {
        //     steps {
        //         script{
        //             test("BOOKS", "PRD")
        //         }
        //     }
        // }
        //         stage('tests-on-prod') {
        //     steps {
        //         script{
        //             test("BOOKS", "PRD")
        //         }
        //     }
        // }
    }
}

def build(){
    echo "Building of node application is starting.."
    git branch: 'main', poll: false, url: 'https://github.com/OlegsBrown/python-greetings.git'
    bat "npm install pm2 -g"
    bat "dir"
    bat "pip3 install -r requirements.txt"
}

// def deploy(String environment, int port){
//     echo "Deployment to ${environment} has started.."
//     git branch: 'main', url: 'https://github.com/OlegsBrown/python-greetings.git'
//     bat "npm install"
//     bat "C:\\Users\\ole6k\\AppData\\Roaming\\npm\\pm2 delete \"books-${environment}\" & EXIT /B 0"
//     bat "C:\\Users\\ole6k\\AppData\\Roaming\\npm\\pm2 start -n \"books-${environment}\" index.js -- ${port}"
// }

// def test(String test_set, String environment){
//     echo "Testing ${test_set} test set on ${environment} has started.."
//     git branch: 'main', poll: false, url: 'https://github.com/OlegsBrown/python-greetings.git'
//     bat "npm install"
//     bat "npm run ${test_set} ${test_set}_${environment}"
// }