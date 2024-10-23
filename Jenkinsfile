pipeline {
    agent none // Don't use a default agent

    stages {
        stage('Build on slave1') {
            agent { label 'slave1' }
            environment {
                JAVA_HOME = '/usr/lib/jvm/java-11-openjdk-amd64' // Specify the JAVA_HOME
            }
            steps {
                sh 'mvn clean package -Dmaven.test.skip=true'
            }
        }
        
        stage('Build on slave2') {
            agent { label 'slave2' }
            environment {
                JAVA_HOME = '/usr/lib/jvm/java-11-openjdk-amd64' // Specify the JAVA_HOME
            }
            steps {
                sh 'mvn clean -Dmaven.test.skip=true'
            }
        }
    }
    
    post {
        success {
            echo 'Archiving the artifacts'
            archiveArtifacts artifacts: '**/target/*.war'
        }
    }
}

