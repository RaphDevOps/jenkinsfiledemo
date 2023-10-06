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
        
        stage('Code Review') {
            steps {
                // Run PMD analysis and store the results in pmd.xml
                sh 'mvn pmd:pmd'
            }
            
            post {
                success {
                    // Record PMD issues
                    recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
                }
            }
        }
    }
}
        
