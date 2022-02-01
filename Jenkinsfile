pipeline
{
     agent any
     stages{
			stage('Continous Downoad')
			   {
				   steps{
						   script
							{
							   try
							   {
								  git branch: 'main', url: 'https://github.com/kailastambe/maven.git'
							   }
							   catch(Exception e1)
							   {
								   mail bcc: '', body: 'CI has Failed', cc: 'jaya.tambe@gmail.com', from: '', replyTo: '', subject: 'Cont download has Failed', to: 'kailashtambe@gmail.com'
								   exit(1)
							   }
							}
					  
						}
				}
			stage('Contnous Build')
			   {
				   steps{
						   script
							{
							   try
							   {
								  sh 'mvn package'
							   }
							   catch(Exception e2)
							   {
								   mail bcc: '', body: 'CI has Failed', cc: 'jaya.tambe@gmail.com', from: '', replyTo: '', subject: 'Cont build has Failed', to: 'kailashtambe@gmail.com'
								   exit(1)
							   }
							}
					   
						}
				}
			  stage('Contnous deploy')
			   {
				   steps{
							script
							{
							   try
							   {
								  sh 'scp /home/ubuntu/.jenkins/workspace/Declarative-pipeline/webapp/target/webapp.war ubuntu@172.31.46.110:/var/lib/tomcat9/webapps/testapp1.war'
							   }
							   catch(Exception e3)
							   {
								   mail bcc: '', body: 'CI has Failed', cc: 'jaya.tambe@gmail.com', from: '', replyTo: '', subject: 'Cont deploy has Failed', to: 'kailashtambe@gmail.com'
								   exit(1)
							   }
							}			   
					
						}
			   }  
			   stage('continous testing')
				{
				   steps{ 
						   script
							{
							   try
							   {
								  git branch: 'main', url: 'https://github.com/kailastambe/Functional-testing.git'
								  sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarative-pipeline/testing.jar'
							   }
							   catch(Exception e4)
							   {
								   mail bcc: '', body: 'CI has Failed', cc: 'jaya.tambe@gmail.com', from: '', replyTo: '', subject: 'Cont testing has Failed', to: 'kailashtambe@gmail.com'
								   exit(1)
							   }
							}	
				   
						}
				} 
			   stage('testingdelivery')
			   {
				   steps{
						   script
							{
							   try
							   {
								  sh 'scp /home/ubuntu/.jenkins/workspace/Declarative-pipeline/webapp/target/webapp.war ubuntu@172.31.44.10:/var/lib/tomcat9/webapps/prodapp1.war'
							   }
							   catch(Exception e5)
							   {
								   mail bcc: '', body: 'CI has Failed', cc: 'jaya.tambe@gmail.com', from: '', replyTo: '', subject: 'Cont build has Failed', to: 'kailashtambe@gmail.com'
								   exit(1)
							   }
							}
						}
			   }
           }  
}
