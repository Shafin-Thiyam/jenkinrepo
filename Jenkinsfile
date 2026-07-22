pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Checkout') {
            steps {
                git url:  'https://github.com/Shafin-Thiyam/sthiyatrend.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    stage('SonarQube analysis') {
        environment{
            scannerHome = tool 'sthiya-sonar-qube-scanner'
        }
        steps {
           withSonarQubeEnv('sthiya-sonar-qube-server'){
            sh "${scannerHome}/bin/sonar-scanner"
           }
}
    }
}
}
