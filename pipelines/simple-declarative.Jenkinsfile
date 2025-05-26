pipeline {
    agent any
    parameters {
        string(name: 'branch', defaultValue: 'main', description: 'The branch to fetch for the pipeline')
    }

    stages {
        stage("SCM"){
            steps {
                    git branch: "${params.branch}", url: 'https://github.com/arjunroy89/declarative-pipelines.git'

                }
            }
        stage('static analysis'){
            steps{
                echo "Perform static analysis"
                sleep time: 3, unit: 'SECONDS'
                }
            }
        stage('build'){
            steps{
                echo "Build the code"
                sleep time: 3, unit: 'SECONDS'
                }
            }

        stage('unit test'){
            steps{
                echo "Execute unit tests"
                sleep time: 3, unit: 'SECONDS'
                }
            }
        stage("Package"){
            steps {
                echo "Packaging the code for release"
            }
        }    
        }
    
}
