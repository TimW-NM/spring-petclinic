pipeline {
    agent any
    tools {
        maven 'the_maven'
        jdk 'jdk8'
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
    post {
        success {
            junit 'target/surefire-reports/**/*.xml'
        
            def uploadSpec = """{
              "files": [
                {
                  "pattern": "/target/spring-petclinic-*.BUILD-SNAPSHOT.jar",
                  "target": "example-repo-local"
                }
             ]
            }"""
            server.upload(uploadSpec)
        }
        
    }
    
}
