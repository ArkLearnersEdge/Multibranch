node('Dev') {
    stage('ContinuousDownload') 
    {
     git 'https://github.com/ArkLearnersEdge/maven.git'
    }
    stage('ContinuousBuild') 
    {
     sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/master/webapp/target/webapp.war ubuntu@172.31.10.108:/var/lib/tomcat8/webapps/testapp.war'
    }
    stage('ContinuousTesting') 
    {
     git 'https://github.com/ArkLearnersEdge/FunctionalTesting.git'
     sh 'java -jar /home/ubuntu/.jenkins/workspace/master@2/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/master/webapp/target/webapp.war ubuntu@172.31.23.247:/var/lib/tomcat8/webapps/Prodapp.war'
    }
  
    
    
    
}
