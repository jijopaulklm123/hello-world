pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }      
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'eu-west-1',credentials:'aws-test-id') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Download(file:'test.txt', bucket:'amytest123', path:'test.txt', force:true)
					  sh 'ls -ltrh'  
                  }
              }
         }
     }
}
