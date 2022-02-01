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
			}
		}	
