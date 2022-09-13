pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                sh 'printenv' 
                echo "${WORKSPACE}/Builds/${env.JOB_NAME}-${env.BUILD_NUMBER}"
                echo "SCM Trigger test done!!"
                slackSend color: '#BADA55', message: 'Hello, World!'
               
                sh'''#!/bin/bash 
                cd /var/lib/jenkins/sqlpackage/
                /var/lib/jenkins/sqlpackage/sqlpackage
                '''
                     
            }
        }
        stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-1',credentials:'arn:aws:iam::872161624847:user/Palavekari.Sumalatha@ibm.com') {
                  sh 'echo "Uploading file S3 bucket"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'test.py', path:'dags/'bucket:'airflowtest-dag')
')
                  }
              }
         }
        
    }
}
