pipeline {
    agent none
    stages {
        stage('apache') {
            agent { 
                docker 'httpd' 
            }
            steps {
                sh 'yum -y install tomcat'
                sh 'yum -y install wget'
                sh 'cd /usr/share/tomcat/webapps'
                sh 'wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war  & \ 
                    systemctl restart tomcat'
                    
            }
        }
        
    }     
}
