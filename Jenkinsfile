pipeline {
    agent any
    stages {

        stage('Build') {
            steps {
                echo("build the war")
            }
        }

        stage("Deploy to QA"){
            steps{
                echo("deploy to qa")
            }
        }

        stage('Checkout') {
            steps {
                git url: 'https://github.com/AnushaGembali/APIPostmanCollections.git'
            }
        }
        stage('Run api test cases') {
            steps {
                sh 'newman run ./RunCollectionMultipleTimesUsingFiles/RunTestsMultipleTimesUsingFilesCol.json -d ./RunCollectionMultipleTimesUsingFiles/csvfile.csv -n 1 -r htmlextra,cli --reporter-htmlextra-export ./results/datadriventest.html'
            }
        }
        stage('Publish HTML Extra Report'){
            steps{
                     publishHTML([allowMissing: false,
                                  alwaysLinkToLastBuild: false, 
                                  keepAll: true, 
                                  reportDir: 'results', 
                                  reportFiles: 'datadriventest.html', 
                                  reportName: 'HTML Extra API Report', 
                                  reportTitles: ''])
            }
        }

        stage("Deploy to PROD"){
            steps{
                echo("deploy to PROD")
            }
        }
    }
}

