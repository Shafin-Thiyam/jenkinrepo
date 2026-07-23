pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('Checkout') {
            steps {
                //git 'https://github.com/Shafin-Thiyam/jenking-war-web-project.git'
                git url:  'https://github.com/Shafin-Thiyam/sthiyatrend.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo"=====build started=========="
                sh 'mvn clean deploy -Dmaven.test.skip=true'
              echo"=====build completed========""
            }
        }
        stage('test') {
            steps {
                echo "unit test started"
                sh 'mvn surefire-report:report'
                echo "unit test completed"
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
