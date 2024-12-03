pipeline
{
agent any
stages
{
 stage('scm checkout')
 { steps { git branch: 'master', url: 'https://github.com/imGorkey/gradle-example' }}

stage('code build')
 {steps { withGradle {
	sh './gradlew clean build'
 } }}

 stage('code deploy to tomcat server')
 {steps { sshagent(['deploy-to-tomcat']) {
	sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.40.38:/usr/share/tomcat/webapps'
 } }}

}
}
