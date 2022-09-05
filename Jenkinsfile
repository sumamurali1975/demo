pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                sh 'printenv' 
                echo "${WORKSPACE}/Builds/${env.JOB_NAME}-${env.BUILD_NUMBER}"
                echo "SCM Trigger test done!!"
                slackSend color: '#BADA55', message: 'Hello, World!'
                sh '''
                
                sqlpackage
                
                '''
                
                
            }
        }
    }
}
