pipeline {
    agent any

    stages {
        stage("SCM") {
            steps {
                git branch: 'main', url: 'https://github.com/arjunroy89/declarative-pipelines.git'
            }
        }
    }
}
