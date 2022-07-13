node('built-in')
{
    stage('Cont_Download')
    {
        git 'https://github.com/raju2128/maven.git'
    }
    stage('Cont_Build')
    {
        sh 'mvn package'
    }
    stage('Cont_Deployment')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/scripted-pipeline/webapp/target/webapp.war ubuntu@172.31.80.16:/var/lib/tomcat9/webapps/testapp.war'
    }
    stage('Cont_Testing')
    {
        git 'https://github.com/raju2128/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/scripted-pipeline/testing.jar'
    }
    stage('Cont_Delevery')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/scripted-pipeline/webapp/target/webapp.war ubuntu@172.31.81.32:/var/lib/tomcat9/webapps/prodapp.war'
    }
}
