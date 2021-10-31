pipeline {
    agent any
    tools {
        maven 'maven_3_8_3'
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
                        artifactId: 'jenkins-example', 
                     classifier: '', 
                     file: '/docker/jenkins_cont/workspace/demo/target/jenkins-example.1.0-SNAPSHOT.jar', 
                     type: 'jar'
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
