node
{
def mavenHome = tool name: "Maven3.6.3"
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
stage('Cloning our Project'){
git branch: 'development', credentialsId: 'b557371b-28d3-4c15-86a8-62ea2b03bbc6', url: 'https://github.com/prakashmcacmt/maven-web-application.git'
}
stage('Build Package'){
sh "${mavenHome}/bin/mvn clean package"
}
  /*
stage('Execute Sonarqube report'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}
stage('Upload artefacts into Nexus'){
sh "${mavenHome}/bin/mvn deploy"
}
stage('Deploy Application in to Tomact Server'){
sshagent(['92b884bf-632d-462d-89df-bf1f0a6d1897']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.127.33.153:/opt/apache-tomcat-9.0.48/webapps/"
}
}
*/
stage("Send Email Notification")
{
 emailext body: '''Build Over..

regards,
E Prakash''', subject: 'Build Over....', to: 'prakashmcacmt@gmail.com'   
}
}
