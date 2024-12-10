pipeline{
    agent any

    environment{
        ARTIFACT_SOURCE_DIRECTORY = "tests/*.xml"
    }
    stages{
        stage('Build'){
            steps{
                echo 'Build the code'
            }
        }
        stage('Test'){
            steps{
                echo 'Execute unit tests'
                echo 'Test data' > 'tests/testresults.xml'
            }
        }
    }
}