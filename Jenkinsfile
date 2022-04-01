pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
				script
				{
					try
					{
						git 'https://github.com/ArkLearnersEdge/maven_demo.git'
					}
					catch(Exception e1)
					{
					mail bcc: '', body: 'in stage C-D Environment stage failure', cc: 'git_group@gmail.com', from: '', replyTo: '', subject: 'CI-CD Failure stage is ContDownload', to: 'gitadmin@gmail.com'
					}
				}
            }
        }
        stage('ContBuild')
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
					 mail bcc: '', body: 'in stage C-Build stage failure', cc: 'mvn_group@gmail.com', from: '', replyTo: '', subject: 'CI-CD Failure stage is ContBuild', to: 'mvnadmin@gmail.com'
					}
				}
            }
        }
        stage('ContDeploy')
        {
            steps
            {
				script
				{
					try
					{
						sh 'scp /home/ubuntu/.jenkins/workspace/Development/webapp/target/webapp.war ubuntu@172.31.80.108:/var/lib/tomcat8/webapps/testapp'
					}
					catch(Exception e3)
					{
						mail bcc: '', body: 'in stage C-Deploy stage is failure', cc: 'systemadmin_group@gmail.com', from: '', replyTo: '', subject: 'CI-CD Failure stage is ContDeploy', to: 'Systemadmin@gmail.com'
					}
				}
            }
        }
        stage('ContTesting')
        {
			steps
            {
				script
				{
					try
					{
						 git 'https://github.com/ArkLearnersEdge/FunctionalTesting.git'
						 sh 'java -jar /home/ubuntu/.jenkins/workspace/Development/testing.jar'
					}
					catch(Exception e4)
					{
						mail bcc: '', body: 'in stage C-Deploy stage is failure', cc: 'systemadmin_group@gmail.com', from: '', replyTo: '', subject: 'CI-CD Failure stage is ContDeploy', to: 'Systemadmin@gmail.com'
					}
				}
            }
        }
	}
	post
	{
		success
		{
			sh 'scp /home/ubuntu/.jenkins/workspace/Development/webapp/target/webapp.war ubuntu@172.31.80.178:/var/lib/tomcat8/webapps/prodapp'
		}
		failure
		{
			mail bcc: '', body: 'in prod Environment stage failure', cc: 'arklearnersedge@gmail.com', from: '', replyTo: '', subject: 'CI-CD Failure Production Environment', to: 'arklearnersedge@gmail.com'
		}
	}
}
