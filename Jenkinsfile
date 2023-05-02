node('built-in')
{
    stage('countinuedownload')
    {
    git 'https://github.com/intelliqittrainings/maven.git'    
    }
    stage('countinuebuild')
    {
    sh 'mvn package'   
    }
    stage('countinuedeployment')
    {
     deploy adapters: [tomcat9(credentialsId: 'cdb57107-2ffe-4c9d-b5c5-9795648bdee7', path: '', url: 'http://172.31.95.249:8080')], contextPath: 'test', war: '**/*.war'  
    }
    stage('countinuetesting')
    {
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh 'java -jar  /var/lib/jenkins/workspace/scriptedpipeline/testing.jar'
    }
    stage('countinuedelivery')
    {
    deploy adapters: [tomcat9(credentialsId: 'cdb57107-2ffe-4c9d-b5c5-9795648bdee7', path: '', url: 'http://172.31.94.133:8080')], contextPath: 'prod', war: '**/*.war'
    }
}
