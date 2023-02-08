node('built-in')
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: '97f350a2-7ccc-459c-86ee-932d93251f3d', path: '', url: 'http://172.31.84.133:8080')], contextPath: 'testapp', war: '**/*.war'
    }    
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/scripted\\ pipeline/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '97f350a2-7ccc-459c-86ee-932d93251f3d', path: '', url: 'http://172.31.90.211:8080')], contextPath: 'prodapp', war: '**/*.war' 
    }
}
