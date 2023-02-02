pipeline {
    agent any
    stages {
        stage('clone') {
            steps {
                git branch: 'DEV', url: 'https://github.com/koti73/mavenproject.git'
            }
        }
    stage('build') {
        steps {
            sh '''mvn package
                '''
        }
        }
    stage('deploy') {
        steps {
           archiveArtifacts artifacts: '**/*.war'
        }
        }
    stage('archieve') {
        steps {
             sh ''' docker build -t kotie .
                    docker run --name kotikw -d -p 5523:8080 kotie:latest
                '''
        }
    }
    }
} 
