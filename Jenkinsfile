pipeline {
    agent any
    stages {
        stage('Setting the variables values') {
         steps {
            sh "sudo chmod +x -R ${env.WORKSPACE}"
            sh "./${WORKSPACE}/script.sh"
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
