pipeline {
    agent any
    stages {
        stage('Prepare'){
            steps {
                git credentialsId : 'github',
                    branch : 'master',
                    url : 'https://github.com/cho04322/helm-sample-app.git'
            }
        }
        stage('test') {
            steps {
                echo 'test stage'
            }
        }
        stage('build') {
            steps {
                echo 'build stage'
            }
        }
        stage('docker build') {
            steps {
                echo 'docker build stage'
            }
        }
    }
}
