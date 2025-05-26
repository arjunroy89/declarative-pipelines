pipeline {
    agent any
    parameters {
        string(name: 'branch', defaultValue: 'main', description: 'The branch to fetch for the pipeline')
    }

    triggers {
        cron('0 3 * * 1-5')
    }
    stages {
        stage("SCM"){
            steps {
                    git branch: "${params.branch}", url: 'https://github.com/arjunroy89/declarative-pipelines.git'

                }
            }
            stage('build'){
                steps{
                    echo "Build the code"
                }
            }
        stage("Package"){
            when {
                expression {
                    return params.branch == "release"
                }
            }
            steps {
                echo "Packaging the code for release"
            }
        }    
        }
    
}
