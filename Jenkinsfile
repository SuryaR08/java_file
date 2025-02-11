pipeline {
    agent { label 'docker-agent' }
 
    stages {
        // stage('Clone Repository') {
        //     steps {
        //         sh 'rm -rf java_file || true'
        //         sh 'git clone -b main https://github.com/SuryaR08/java_file.git'
        //     }
        // }
        stage('Run') {
            steps {
                dir('java_file'){
                   sh 'javac hello.java'
                   sh 'java hello' 
                }
                
            }
        }
    }
}
