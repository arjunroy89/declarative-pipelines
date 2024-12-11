pipeline{
    agent any

    environment{
        ARTIFACT_SOURCE_DIRECTORY = "tests/*.xml"
        ORG = 'OurWebCompany'
        PROJECT = 'OurNewApplication'
        PIPELINE = 'ado-deployer'
        PAT = credentials('ado-pat')
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
                sh 'mkdir -p tests && echo "test results" > tests/testresults.xml'
                error "Broken tests break the build"
            }
        }
    }
    post{
        always{
            archiveArtifacts artifacts: ARTIFACT_SOURCE_DIRECTORY, followSymlinks: false

            echo 'Upload the artifact to Azure Storage'

            script{
                // POST https://dev.azure.com/{organization}/{project}/_apis/pipelines/{pipelineId}/runs?api-version=7.1

                def targetURL = "https://dev.azure.com/${env.ORG}/${env.PROJECT}/_apis/pipelines/${env.PIPELINE}/runs?api-version=7.1"

                def response = httpRequest(
                    httpMode: 'POST', 
                    url: targetURL,
                    customHeaders: [[name: 'Authorization', value: "Basic ${env.PAT.tokenize(':').collect {it.bytes.encodeBase64().toString()}.join(':')}"]],
                    contentType: "APPLICATION_JSON", 
                    requestBody: '{}'
                )
            }

            echo 'Deployment triggered'
        }
    }
}