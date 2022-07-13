pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/raju2128/maven.git'
            }    
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }    
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/declrative-pipeline/webapp/target/webapp.war ubuntu@172.31.80.16:/var/lib/tomcat9/webapps/testapp.war'
            }    
        }
        stage('ContinuousTesting')
        {
            steps
            {
               git 'https://github.com/raju2128/FunctionalTesting.git'
               sh 'java -jar /home/ubuntu/.jenkins/workspace/declrative-pipeline/testing.jar'
            }
        }
        stage('ContinuousDelevery')
        {
            steps
            {
               sh 'scp /home/ubuntu/.jenkins/workspace/declrative-pipeline/webapp/target/webapp.war ubuntu@172.31.81.32:/var/lib/tomcat9/webapps/prodapp.war' 
            }
        }
    }
}
