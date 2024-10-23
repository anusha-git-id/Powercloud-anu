pipeline {
    agent none // Don't use a default agent

    stages {
        stage('Build on Slave1') {
            agent { label 'Slave1' } // Specify that this stage runs on Slave1
            steps {
                // Run Maven clean and package, skipping the tests
                sh 'mvn clean package -Dmaven.test.skip=true'
            }
        }
        
        stage('Build on Slave2') {
            agent { label 'Slave2' } // Specify that this stage runs on Slave2
            steps {
                // Run Maven clean and package, skipping the tests
                sh 'mvn clean package -Dmaven.test.skip=true'
            }
        }
    }
    
    post {
        success {
            echo 'Archiving the artifacts'
            // Archive artifacts after both builds
            archiveArtifacts artifacts: '**/target/*.war'
        }
    }
}

