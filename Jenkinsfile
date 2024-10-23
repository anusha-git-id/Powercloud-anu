pipeline {
    agent any

    

    stages {
        stage('Build') {
            steps {
                // Run Maven clean and package, skipping the tests
                sh 'mvn clean package -Dmaven.test.skip=true'
            }
        }
    }
    
    post {
        success {
            echo 'Archiving the artifacts'
            // Correct the archiveArtifacts syntax
            archiveArtifacts artifacts: '**/target/*.war'
        }
    }
}
