pipeline
{
    agent any
    stages
    {
        stage ('continuos_Download')
        {
            steps
            {
              git 'https://github.com/IntelliqDevops/maven1.git'  
            }
        }
        stage ('continuos_Build')
        {
            steps
           {
            sh 'mvn package'
           }  
        }
        stage ('continuos_deploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'f93c1a56-c58d-460c-a340-5e1bbbdb010f', path: '', url: 'http://172.31.6.181:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage ('continuos_testing')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
            }
        }
        stage ('Continuos_Delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'f93c1a56-c58d-460c-a340-5e1bbbdb010f', path: '', url: 'http://172.31.5.89:8080')], contextPath: 'production', war: '**/*.war'
            }
        }
    }
}
