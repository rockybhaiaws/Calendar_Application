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

                 mvn package
            }
        }
        stage('Post Build') {
            steps {
                echo "Build Successfully Completed"
                java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App
            }
        }
    }
}
