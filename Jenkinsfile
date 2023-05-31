pipeline {
    agent any
    stages {
        stage('Setting the variables values') {
         steps {
            sh '/home/alvaro/Desktop/script.sh'
         }
      }
        stage('Test') {
            steps {
                echo 'Test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy'
            }
        }
    }
}
