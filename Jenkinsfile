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
        
        stage('Compile Code') {
            steps {
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
     
