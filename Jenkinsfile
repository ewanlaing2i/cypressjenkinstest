// pipeline{

//     agent any

//     parameters{
//         string(name: 'SPEC', defaultValue: "cypress/integration/**/**", description: "Enter the scripts path that you want to execute")
//         choice(name: 'BROWSER', choices: ['chrome', 'edge', 'firefox'], description: "Choose the browser to execute scripts")
//     }

//     // options{
//     //     ansiColor('xterm')
//     // }

//     stages{
//         stage('Building'){
//             steps{
//                 echo "Building application"
//             }
            
//         }
//         stage('Testing'){
//             steps{
//                 bat "npm i"
//                 bat "npx cypress run --browser=${BROWSER} --spec=${SPEC}"
//             }
//         }
//         stage('Deploying'){
//             steps{
//                 echo "Deploying application"
//             }
//         }
//     }

// }


pipeline {
    agent any
 
    stages {
        stage('Checkout and Install Dependencies') {
            steps {
                script {
 
                    // Install project dependencies including Cypress
                    bat 'npm install'
                }
            }
        }
 
        stage('Run Cypress Tests') {
            steps {
                script {
                    //TEST
                    // Run Cypress tests
                    bat 'npx cypress run --spec cypress/e2e/mainTest.cy.js'
                }
            }
        }
    }

    post{
        always{
            publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
        }
    }
}