node('master') {
   stage('Continuous Download')
   {
     git 'https://github.com/krishnamaggi/Maven.git' 
   }
    stage('Continuous Build')
   {
     sh 'mvn package'
   }
    stage('Continuous Deployment')
   {
     sh 'scp /var/lib/jenkins/workspace/PipelineJob/webapp/target/webapp.war krishna1@192.168.136.131:/var/lib/tomcat/webapps/testapp.war'
   }
    stage('Continuous Testing')
   {
     git 'https://github.com/krishnamaggi/FunctionalTesting.git'
     sh 'java -jar /var/lib/jenkins/workspace/PipelineJob/testing.jar'
   }
   stage('Continuous Delivery')
   {
     input message: 'Waiting for Approval from DM  ', submitter: 'maggi'
     sh 'scp /var/lib/jenkins/workspace/PipelineJob/webapp/target/webapp.war krishna2@192.168.136.132:/var/lib/tomcat/webapps/prodapp.war'
   }
}
