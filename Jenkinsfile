pipeline
{
    agent any
    stages
    {
        stage('C.Download')
        {
            steps
            {
                script
                {
                 try
                 {
                    git 'https://github.com/ArkLearnersEdge/maven.git'
                 }
                 catch(Exception e1)
                 {
                      mail bcc: '', body: 'stage 1 failed to download url from git', cc: 'scrum_admingrp@gmailcom', from: '', replyTo: '', subject: 'failed to download', to: 'scrum_1@gmail.com' 
                 }
            
                }
            }
        }
        stage('C.Build')
        {
            steps
            {
                script
                {
                 try
                 {
                    sh 'mvn package'
                 }
                 catch(Exception e2)
                 {
                      mail bcc: '', body: 'stage 2 failed to build at maven', cc: 'scrum_admingrp@gmailcom', from: '', replyTo: '', subject: 'failed to build', to: 'scrum_1@gmail.com'
                 }
            
                }
            }
        }
        stage('C.Deploy')
        {
            steps
            {
                script
                {
                 try
                 {
                    sh 'scp /home/ubuntu/.jenkins/workspace/dec1/webapp/target/webapp.war ubuntu@172.31.85.205:/var/lib/tomcat8/webapps/testapps'
                 }
                 catch(Exception e3)
                 {
                     mail bcc: '', body: 'stage 3 failed to Deploy at testing tomcat8', cc: 'scrum_admingrp@gmailcom', from: '', replyTo: '', subject: 'failed to Deploy', to: 'scrum_1@gmail.com'
                 }
            
                }
            }
        }
        stage('C.Testing')
        {
            steps
            {
                script
                {
                 try
                 {
                     git 'https://github.com/ArkLearnersEdge/FunctionalTesting.git'
                     sh 'java -jar /home/ubuntu/.jenkins/workspace/dec1/testing.jar'
                 }
                 catch(Exception e4)
                 {
                     mail bcc: '', body: 'stage 3 failed to Testing copy url in git and testing tomcat8', cc: 'scrum_admingrp@gmailcom', from: '', replyTo: '', subject: 'failed to testing', to: 'scrum_1@gmail.com'
                 }
            
                }
            }
        }
	}
		
	post
    {
        success
       
        {
            sh 'scp /home/ubuntu/.jenkins/workspace/dec1/webapp/target/webapp.war ubuntu@172.31.88.159:/var/lib/tomcat8/webapps/prodapps'
        }
        failure
        {
           mail bcc: '', body: 'stage 5 failed to delivery ', cc: 'scrum_admingrp@gmailcom', from: '', replyTo: '', subject: 'failed to delivery in production', to: 'scrum_1@gmail.com'
        }
            
           
    }
}
