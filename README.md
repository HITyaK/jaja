# jaja

pipeline{
    agent any
    tools{
        maven "MAVEN_HOME"
    }
    
    stages{
        stage("git repo & clean"){
            steps{
                bat "rmdir /s /q SampleMavenJavaProject"
                bat "git clone https://github.com/lalithacharannukaraju/SampleMavenJavaProject.git"
                bat "mvn clean -f SampleMavenJavaProject"
            }
        }
        stage("install"){
            steps{
                bat "mvn install -f SampleMavenJavaProject"
            }
        }
        stage("test"){
            steps{
                bat "mvn test -f SampleMavenJavaProject"
            }
        }
        stage("package"){
            steps{
                bat "mvn package -f SampleMavenJavaProject"
            }
        }
        
    }
}
