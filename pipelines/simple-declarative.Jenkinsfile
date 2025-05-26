pipeline {
    agent any
    triggers{
        cron('0 3 * * 1-5')
    }

    stages {
         stage('build'){
            steps{
                echo 'build the code'
                    }
                }
        stage('Package') {
            when {
                expression {
                    return params.branch == "release"
                }
            }
            steps {
                echo 'Packaging the code for release'
            }
        }
    }
}
