pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo"Archiving the Artifacts"
                    archiveArtifacts artifacts:'**/target/*.war'
                }
            }

        }
        stage ('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat9(credentialsId: '02a78b00-4c60-4ab1-833c-bb8d31c3e5d0', path: '', url: 'http://192.168.1.247:8080/')], contextPath: null, war: '**/*.war'
            }

        }
    }
}