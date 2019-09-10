node('master')
{
    stage('ContinuousDownload') 
    {
         git 'https://github.com/saladimadhu/mavan.git'
    }
    stage('ContinuousBuild') 
    {
         sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/pipeline/webapp/target/webapp.war ubuntu@172.31.0.168: /var/lib/tomcat8/webapps/testenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/saladimadhu/testing.git'
        sh label: '', script: 'echo "testing passed"'
    }
     stage('ContinuousDelivery')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/pipeline/webapp/target/webapp.war ubuntu@172.31.10.205: /var/lib/tomcat8/webapps/prodenv.war'
    }
    
    
}

