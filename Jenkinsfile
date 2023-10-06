pipeline {
    agent any
    
    tools {
        // Define the Maven tool named 'mymaven'
        maven 'mymaven'
    }
    stages {
        stage('Clone Repos') {
            steps {
                // Clone the Git repository
                git url: 'https://github.com/RaphDevOps/PURDUE-DevOpsCodeDemo.git'
            }
        }
        
        stage('Compile Code') {
            steps {
                // Compile the code using Maven
                sh 'mvn compile'
            }
        }
        
        stage('code review') {
            steps {
                sh 'mvn pmd:pmd'
            }
            post {
                
                success{
                    recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
                }
            }
        }
        
        stage('Test Code') {
            steps {
                // Run tests using Maven
                sh 'mvn test'
            }
            post{
                success{
                    
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Package Code') {
            steps {
                // Package the code using Maven
                sh 'mvn package'
            }
        }
    }
}
