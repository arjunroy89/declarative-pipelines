pipeline {
    agent any

    tools {
        // Ensure this matches the name configured in Jenkins > Global Tool Configuration
        jdk 'openjdk-21'            
        maven 'maven-3.9.10'
    }

    environment {
        JAVA_HOME = tool 'openjdk-21'
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
