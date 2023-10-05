def registry = 'https://valaxy05.jfrog.io'
def imageName = 'valaxy05.jfrog.io/valaxy-docker-local/ttrend'
def version   = '2.1.4'
pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.4/bin:$PATH"
}
    stages {
        stage("build"){
            steps {
                 echo "----------- build started ----------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                 echo "----------- build complted ----------"
            }
        }
    stage{
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
