pipeline {
    agent any
    
    environment {
        SENTENCE = "I hope you do well in future"
    }
    stages {
        stage("Hello"){
            steps {
                echo 'Hello, world.!'
                
                script {
                    def words = env.SENTENCE.split(' ')
                    
                    for (word in words){
                        echo word
                    }
                    
                }
            }
        }
    }
    
}
