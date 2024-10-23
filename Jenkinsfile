pipeline {
    agent none // Use 'none' to define stages with their own agents

    stages {
        stage('Build on Slave1') {
            agent { label 'slave1' } // Specify the agent for this stage
            tools {
                maven 'Maven3' // Use the configured Maven tool name
            }
            steps {
                // Run Maven clean and package, skipping the tests
                sh 'mvn clean package -Dmaven.test.skip=true'
            }
        }
        
        stage('Build on Slave2') {
            agent { label 'slave2' } // Specify the agent for this stage
            tools {
                maven 'Maven3' // Use the configured Maven tool name
            }
            steps {
                // Run Maven clean and package, skipping the tests
                sh 'mvn clean package -Dmaven.test.skip=true'
            }
        }
    }
    
    post {
        success {
            echo 'Archiving the artifacts'
            // This needs to be inside a node context. Adding node block for archiving.
            node {
                archiveArtifacts artifacts: '**/target/*.war'
            }
        }
    }
}
