pipeline {
    agent any 
    
    environment {
    }
    
    stages {
        stage('SCM'){
            steps {
                   git branch: 'main', url: 'https://github.com/FeynmanFan/declarative-pipelines.git'
            }
        }
    }
}