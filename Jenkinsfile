pipeline{
    agent any
    stages{
        stage('Download'){
            steps{
                git credentialsId: 'Ashok', url: 'https://github.com/karthikDec29/onlinebookstore-master.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Deploy'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'Ashok', path: '', url: 'http://54.146.50.185:8000/')], contextPath: 'matha', war: '**\\*.war'
            }
        }
        stage('Testing'){
            steps{
            git 'https://github.com/karthikDec29/FunctionalTesting.git'
            sh 'java -jar /var/lib/jenkins/workspace/Declarative_pipeline/testing.jar'           
            }
        }
        stage('Delivery'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'Ashok', path: '', url: 'http://54.146.50.185:8000/')], contextPath: 'matha', war: '**\\*.war'
            }
        }
    }
}
