pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Checkout') {
            steps {
                //git 'https://github.com/Shafin-Thiyam/jenking-war-web-project.git'
                git url:  'https://github.com/Shafin-Thiyam/jenking-war-web-project.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube analysis') {
            environment{
                scannerHOME = tool 'sthiya-sonar-qube-scanner'
            }
            steps {
                withSonarQubeEnv('sthiya-sonar-qube-server'){
                sh "${scannerHOME}/bin/sonar-scanner"
                }
            }
        }
        
        
    }
}
