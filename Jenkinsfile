pipeline
{
    agent any
    stages
    {
        stage (CD)
        {
            steps
            {
                git 'https://github.com/GK4752/Rama.git'
            }
        }
        stage (CB)
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage (CDeploy)
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'c84b776c-4cfd-4124-a47b-d0ec7608a9de', path: '', url: 'http://172.31.8.101:8080')], contextPath: 'testweb', war: '**/*.war'
            }
        }
        stage (CTesting)
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/ProjectGK/testing.jar'
            }
        }
        stage (CDelivery)
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'c84b776c-4cfd-4124-a47b-d0ec7608a9de', path: '', url: 'http://172.31.16.39:8080')], contextPath: 'prodweb', war: '**/*.war'
            }
        }
        
    }
}
