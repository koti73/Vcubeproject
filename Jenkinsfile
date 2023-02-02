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
            deploy adapters: [tomcat9(credentialsId: '8f923185-5e4f-4d2d-ae92-96e32c4535db', path: '', url: 'http://54.146.81.45:8080/')], contextPath: null, war: '**/*.war'
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
