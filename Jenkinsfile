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
		stage('Prepare Newman Results Directory') {
            steps {
                sh 'mkdir -p $(pwd)/newman' 
            }
        }
        stage('Pull Image from Docker') {
            steps {
                sh 'docker pull anushabellala/datadriventest:1.0'
            }
        }
        stage('Run api test cases') {
            steps {
				sh 'docker run --rm -v $(pwd)/newman:/app/results/ anushabellala/datadriventest:1.0'
            }
        }
        stage('Publish HTML Extra Report'){
            steps{
                     publishHTML([allowMissing: false,
                                  alwaysLinkToLastBuild: false, 
                                  keepAll: true, 
                                  reportDir: 'newman', 
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

