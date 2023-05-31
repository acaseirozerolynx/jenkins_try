pipeline {
    agent any
    stages {
        stage('Setting the variables values') {
         steps {
            sh "chmod +x -R ${env.WORKSPACE}"
            sh "./home/alvaro/Desktop/script.sh"
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
