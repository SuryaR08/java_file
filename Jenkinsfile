pipeline {
    agent {
        label 'docker-agent'
    }
    options {
        skipDefaultCheckout(true)
    }
    environment {
        GIT_EXECUTABLE = '/usr/bin/git'  
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    gitTool(name: 'git', home: env.GIT_EXECUTABLE)
                }
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'javac hello.java'
                sh 'java hello'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '*.class', fingerprint: true  
            }
        }
    }
    post {
        always {
            cleanWs()  // Clean workspace after execution
        }
    }
}
