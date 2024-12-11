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
                // error "Broken tests break the build"
            }
        }
    }
    post{
        always{
            archiveArtifacts artifacts: ARTIFACT_SOURCE_DIRECTORY, followSymlinks: false

            echo 'Upload the artifact to Azure Storage'

            script{
                //POST https://dev.azure.com/{organization}/{project}/_apis/build/builds?api-version=6.1-preview.7

                def targetURL = "https://dev.azure.com/${env.ORG}/${env.PROJECT}/_apis/build/builds?api-version=6.1-preview.7"

                def requestBody = [
                    definition: [id: env.PIPELINE]
                ]

                def response = httpRequest(
                    httpMode: 'POST', 
                    url: targetURL, 
                    contentType: 'APPLICATION_JSON',
                    customHeaders: [[name: 'Authorization', value: "Basic ${env.PAT.tokenize(':').collect { it.bytes.encodeBase64().toString() }.join(':')}"]],
                    requestBody: groovy.json.JsonOutput.toJson(requestBody)
                )

                if (response.status == 200 || response.status == 201()){
                    echo "Build queued"
                }else{
                    error "Build failed to queue"
                }
            }
        }
    }
}