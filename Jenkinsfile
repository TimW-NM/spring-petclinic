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
        }
    }
}
