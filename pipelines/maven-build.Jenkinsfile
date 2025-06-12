pipeline{
    agent any
    tools{
        maven 'maven-3.9.10'
    }
    stages{
        stage('Maven version'){
            steps{
                sh 'mvn --version'
            }
        }
    }
}
