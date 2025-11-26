pipeline {
    agent any

    tools {
        maven 'maven'   // must match Jenkins tool name
    }

    triggers {
        githubPush()    // auto trigger webhook
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/SriharshaG05/java-webapp.git', branch: 'main'
            }
        }

        stage('Build WAR') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Archive WAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
    }
}
