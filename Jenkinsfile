pipeline {
    agent { label 'docker-agent' }

    environment {
        GIT_EXECUTABLE = '/usr/bin/git'  // Force Git inside the Docker agent
    }

    stages {
        stage('Verify Git') {
            steps {
                script {
                    sh 'which git'
                    sh 'git --version'
                }
            }
        }

        stage('Checkout Code') {
            steps {
                script {
                    checkout([$class: 'GitSCM', 
                        branches: [[name: '*/main']], 
                        userRemoteConfigs: [[
                            url: 'git@github.com:SuryaR08/java_file.git'
                        ]],
                        gitTool: 'Default'  
                    ])
                }
            }
        }

        stage('Hello') {
            steps {
                echo 'Hello from Jenkins Agent!'
            }
        }
    }
}
