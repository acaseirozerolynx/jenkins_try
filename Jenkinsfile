pipeline {
    agent any
    stages {
        stage('Setting the variables values') {
         steps {
            sh '''
          #!/bin/bash
          pwd
          ls
          ./script.sh
        '''
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
