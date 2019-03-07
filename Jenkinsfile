#! /vagrant

pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('build') {
            steps {
                sh 'echo  starting ...'
                sh 'mvn --version'
                sh 'echo ending...'
            }
        }
    }
}
