pipeline {
    agent any
    tools {
        maven 'maven3_8_3'
    }

    stages {
        stage ('Compile Stage') {

            steps {
                
                    sh 'mvn clean package'
                }
        }
        
        stage ('Upload to nexus') {
            
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app', 
                     classifier: '', 
                     file: 'target/simple-app.war', type: 'war'
                    ]
                ], 
                    credentialsId: 'nexus-credentiels', 
                    groupId: 'com.techprimers.testing',
                    nexusUrl: '192.168.1.8:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http',
                    repository: 'demo', 
                    version: '1.0-SNAPSHOT'
            }
        }

    }
}
