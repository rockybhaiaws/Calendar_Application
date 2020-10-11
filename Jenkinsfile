pipeline {
    agent any

    stages {
        stage('Pull Code') {
            steps {
                // Get some code from a GitHub repository
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'tomcatuser', url: 'https://github.com/rockybhaiaws/Calendar_Application.git']]])
            }
        }
        stage('Build') {
            steps {

                 sh '''sh /var/lib/jenkins/test.sh'''
            }
        }
        stage('Post Build') {
            steps {
                echo "Build Successfully Completed"
            }
        }
    }
}
