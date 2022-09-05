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
                wget 'https://go.microsoft.com/fwlink/?linkid=2196335'
                cd ~
                mkdir sqlpackage
                unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
                echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
                chmod a+x ~/sqlpackage/sqlpackage
                source ~/.bashrc
                sqlpackage
                
                '''
                
             
                
                
            }
        }
    }
}
