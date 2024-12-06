pipeline {
    agent any
    parameters{
        string(name:'branch', defaultValue:'main', description: 'The branch to fetch for the pipeline')
    }
    
    triggers{
        cron('0 3 * * 1-5')
    }

    stages {
        stage('SCM'){
            steps {
                git branch: 'main', url: 'https://github.com/FeynmanFan/declarative-pipelines.git'
            }
        }
        stage('build'){
            steps{
                echo "Build the code"
                // build the code
            }
        }
        stage('Package'){
            when {
                branch 'release'
            }
            steps{
                echo 'Packing the code'
            }
        }
    }
}
