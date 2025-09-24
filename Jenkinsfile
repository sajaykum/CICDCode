pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeploy')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '8c326b60-2a65-4b6b-8954-8ca3f4d4a7a2', path: '', url: 'http://13.52.248.150:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar  /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
             deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '4893cfc4-81bd-462c-ac8a-d2e20756102b', path: '', url: 'http://54.153.14.29:8080')], contextPath: 'test1', war: '**/*.war'   
            }
        }
        
}
            
}
