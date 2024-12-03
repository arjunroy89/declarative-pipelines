pipeline {
    agent any 
    
    environment {
        SENTENCE = "I hope your brother's El Camino runs forever"
    }
    
    stages {
        stage('Hello'){
            steps {
               echo 'Hello World!'
               
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