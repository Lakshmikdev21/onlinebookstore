pipeline {
    agent any
 
    stages {
        stage('Clone') {
            steps {
                git branch: 'feature/2025.06.13', credentialsId: 'github', url: 'https://github.com/Lakshmikdev21/onlinebookstore.git'
            }
        }
          stage('Build') {
            steps {
               bat 'mvn clean install'
            }
        }
          stage('Generate Artifacts') {
            steps {
               archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }
		stage('Deploy to Tomcat Server') {
        steps {
            deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'Tomcat', path: '', url: 'http://localhost:8080')], contextPath: 'GLK ONLINEBOOKSTORE', war: 'target/*.war'
        }
    }
    }
}