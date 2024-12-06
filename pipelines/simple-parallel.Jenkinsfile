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

        stage('build') {
            steps {
                echo 'build the code'
                // build the code
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the code for release'
            }
        }
    }
}