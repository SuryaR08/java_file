pipeline {
    agent { label 'docker-agent' }
    
    environment {
        GIT_EXECUTABLE = '/usr/bin/git'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    def gitToolHome = isUnix() ? '/usr/bin/git' : 'C:\\Program Files\\Git\\bin\\git.exe'
                    withEnv(["GIT_EXECUTABLE=${gitToolHome}"]) {
                        checkout scm
                    }
                }
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
            cleanWs()
        }
    }
}
