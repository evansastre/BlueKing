#! /vagrant

pipeline {
    agent none
    stages {
        stage('java') {
            agent { 
                docker 'maven:3.3.3' 
            }
            steps {
                sh 'echo  starting ...'
                sh 'mvn --version'
                sh 'echo ending...'
            }
        }
        stage('php') {
            agent { 
                docker 'php'
            }
            steps {
                sh 'echo  starting ...'
                sh 'php --version'
                sh 'echo ending...'
            }
        }
    }
        
      
}
