pipeline {
    agent any
    stages {
        stage('Setting the variables values') {
         steps {
            sh '''#!/bin/bash
                 echo "hello world" 
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
