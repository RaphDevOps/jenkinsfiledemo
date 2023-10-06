pipeline {
    agent any
    
    tools {
        // Define the Maven tool named 'mymaven'
        maven 'mymaven'
    }
    stages {
        stage('Clone Repos') {
            steps {
                git url: 'https://github.com/RaphDevOps/PURDUE-DevOpsCodeDemo.git'
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
        
      
