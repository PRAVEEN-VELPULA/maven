node('master') 
{
 stage("ContinuousDownload")
 {
     git 'https://github.com/selenium-saikrishna/maven.git'
 }
 stage("ContinuousBuild")
 {
     sh 'mvn package'
 }
 stage("ContinuousDeployment")
 {
     
     sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.16.206:/var/lib/tomcat7/webapps/qaenv.war'
 }
 stage("ContinuousTesting")
 {
     git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
 }
 stage("ContinuousDelivery")
 {
     input message: 'Waiting for approval from the DM', submitter: 'velpula'
     sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.26.165:/var/lib/tomcat7/webapps/prod.war'

 }
}
