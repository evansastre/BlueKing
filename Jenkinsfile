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
    agent { docker 'php' }
    stages {
        stage('build') {
            steps {
                sh 'echo  starting ...'
                sh 'php --version'
                sh 'echo ending...'
            }
        }
    }
}
