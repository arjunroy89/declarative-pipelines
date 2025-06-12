pipeline {
    agent any

    tools {
        maven 'maven-3.9.10'
    }

    environment {
        JAVA_HOME = "/opt/homebrew/opt/openjdk@21"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Java & Maven Version Check') {
            steps {
                sh 'java -version'
                sh 'mvn --version'
            }
        }
    }
}
