import groovy.json.JsonSlurperClassic

pipeline {
    agent any
        environment {
            USER_CREDENTIALS = credentials('JenkinsTestDD')
        }
    stages {
        stage('Setting the variables values') {
         steps {
            sh '''
          #!/bin/bash
          #docker run -v /home/alvaro/Desktop/:/path zricethezav/gitleaks:latest detect --source="/path/VAmPI/api_views/" -c="path/gitleaks/my_config.toml" --no-git -r="path/gitleaks/report.txt"
          pwd
        '''
         }
      }
        stage('Test') {
            steps {
                script {
                    Object lib = load 'Demo.groovy'
 
                    filePath = "/var/lib/jenkins/workspace/example_master/report.txt"
                    def data = new JsonSlurperClassic().parseText(new File(filePath).text)
                    def productTypeName = "Product_type_jenkins"
                    def productName = "Product_jenkins"
                    def engagementName = "Engagement_jenkins"
                    def testName = engagementName + "_test_" + new Date().getDateTimeString().split(',')[0]
                    //Object DefectDojo = lib.ddPostToken('http://127.0.0.1:8080', "$USER_CREDENTIALS_USR", "$USER_CREDENTIALS_PSW")
                    if (lib.ddPostToken('http://127.0.0.1:8080', "$USER_CREDENTIALS_USR", "$USER_CREDENTIALS_PSW") != 0) { return }
                    if (lib.ddCreateProductType(productTypeName) != 0) { return }
                    if (lib.ddCreateProduct(productName, productTypeName) != 0) { return }
                    if (lib.ddCreateEngagement(engagementName, productName) != 0) { return }
                    if (lib.ddCreateTest(testName, engagementName) != 0) { return }
                    def testID = lib.ddGetTestByName(testName)
                    if (testID != -1) {
                        for (int i = 0; i < data.size(); i++) {
                            if (lib.ddCreateFinding(data[i] , testID) != 0) { return }
                        }
                    }
               }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy'
            }
        }
    }
}
