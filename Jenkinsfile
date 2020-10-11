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
                sh '''sh /var/lib/jenkins/filesystem.sh'''
            }
        }
        stage('Post Build') {
            steps {
                echo "Build Successfully Completed"
                deploy adapters: [tomcat8(credentialsId: 'tomcatuser', path: '', url: 'http://192.168.146.131:8081')], contextPath: '/Calendar', war: '**/*.war'
            }
        }
    }
}
