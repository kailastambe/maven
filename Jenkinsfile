node('master') {
    stage('continous download') {
    git branch: 'main', url: 'https://github.com/kailastambe/maven.git'
    }
    stage('continous build') {
    sh 'mvn package'
    }
    stage('continous deployment') {
    sh 'scp /home/ubuntu/.jenkins/workspace/scripted-pipeline/webapp/target/webapp.war ubuntu@172.31.46.110:/var/lib/tomcat9/webapps/testapp.war'
    }
    stage('continous testing') {
    git branch: 'main', url: 'https://github.com/kailastambe/Functional-testing.git'
    sh 'java -jar /home/ubuntu/.jenkins/workspace/scripted-pipeline/testing.jar'
    }
    stage('continous delivery') {
       
    sh 'scp /home/ubuntu/.jenkins/workspace/scripted-pipeline/webapp/target/webapp.war ubuntu@172.31.44.10:/var/lib/tomcat9/webapps/prodapp.war'    
    }
}
