pipeline {
    agent any
    parameters {
        string(name: 'branch', defaultValue: 'main', description: 'The branch to fetch for the pipeline')
    }

    stages {
        stage('SCM') {
            steps {               
                git branch: '${branch}', url: 'https://github.com/FeynmanFan/declarative-pipelines.git'
            }
        }
        stage('static analysis'){
            steps {
                echo 'perform static analysis'
                sleep time: 3, unit: 'SECONDS'
            }
        }
        stage('build') {
            steps {
                echo 'build the code'
                sleep time: 3, unit: 'SECONDS'
                // build the code
            }
        }
        stage('unit test'){
            steps{
                echo 'execute unit tests'
                sleep time: 3, unit: 'SECONDS'
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging the code for release'
            }
        }
    }
}