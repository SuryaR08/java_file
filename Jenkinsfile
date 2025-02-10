pipeline {
    agent { label 'docker-agent' }


    stages {
        stage('Checkout') {
            steps {
                script {
                        checkout scm
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
