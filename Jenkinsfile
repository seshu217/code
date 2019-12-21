node('master')
{
    stage('continuousdownload')
    {
    git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('continuousbuild')
    {
    sh label: '', script: 'mvn package'
    }
    stage('continuousdeployment')
    {
    sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.43.102:/var/lib/tomcat8/webapps/testapp.war'    
    }
    stage('continuoustesting')
    {
    git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
    sh label: '', script: 'java -jar testing.jar'
    }
    stage('continuousdelivery')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.33.23:/var/lib/tomcat8/webapps/prodapp.war'
    }
    
}
