#! /vagrant

pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo 'Building'
                sh 'echo "hello world"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        
    }
}
