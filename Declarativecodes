pipeline
{
    agent any
    stages 
    {
        stage('ContinuosDownload')
        {
            steps
            {
              git 'https://github.com/prashantgaur985/maven.git'  
            }
        }
        stage('ContinuosBuild')
        {
            steps
            {
              sh 'mvn package'  
            }
        }
        stage('ContinuosDeploment')
        {
            steps
            {
              deploy adapters: [tomcat9(credentialsId: '67e68b6c-1b8d-4dd1-9ea8-a481740a0a27', path: '', url: 'http://172.31.4.137:8080')], contextPath: 'mytestapp', war: '**/*.war'  
            }
        }
        stage('ContinuosTesting')
        {
            steps
            {
             
              git 'https://github.com/prashantgaur985/FunctionalTesting.git'
              sh 'java -jar /var/lib/jenkins/workspace/DeclearativePipeline1/testing.jar'
            }
        }
        stage('ContinuosDelivery')
        {
            steps
            {
              deploy adapters: [tomcat9(credentialsId: '67e68b6c-1b8d-4dd1-9ea8-a481740a0a27', path: '', url: 'http://172.31.14.75:8080')], contextPath: 'myprodapp', war: '**/*.war'  
            }
        }
        
    }
}
