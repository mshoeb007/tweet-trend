def registry = 'https://valaxy05.jfrog.io'
def imageName = 'valaxy05.jfrog.io/valaxy-docker-local/ttrend'
def version   = '2.1.4'
pipeline {
    agent {
        node {
            label 'Jenkins-slave-label'
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.5/bin:$PATH"
    }
    stages {
        stage("build"){
            steps {
                sh 'mvn clean deploy'
            }
        }
    } 
}
