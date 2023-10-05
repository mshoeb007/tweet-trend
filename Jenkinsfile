def registry = 'https://valaxy05.jfrog.io'
def imageName = 'valaxy05.jfrog.io/valaxy-docker-local/ttrend'
def version   = '2.1.4'
pipeline {
    agent {
        node {
            label 'JenkinsSlave'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.4/bin:$PATH"
}
    stages {
        stage("build"){
            steps {
                sh 'mvn clean deploy'
            }
        }
    stage('SonarQube Test'){
        environment{
            scannerHome = tool 'md-sonar-scanner'
        }
        steps{
            withSonarQubeEnv('md-sonarqube-server'){
                sh '${scannerHome}/bin/sonar-scanner'
            }
        }
    }
}
    
}
