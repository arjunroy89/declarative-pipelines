pipeline {
    agent any
    parameters {
        string(name: 'branch', defaultValue: 'main', description: 'The branch to fetch for the pipeline')
    }

    triggers{
        cron('0 3 * * 1-5')
    }

    stages {
        stage('SCM') {
            steps {
                git branch: "${branch}", url: 'https://github.com/FeynmanFan/declarative-pipelines.git'
            }
        }

        stage('Build') {
            steps {
                echo 'build the code'
                // build the code
            }
        }

        stage('Package') {
            when {
                expression {
                    return branch == 'release'
                }
            }
            steps {
                echo 'Packaging the code for release'
            }
        }
    }
}