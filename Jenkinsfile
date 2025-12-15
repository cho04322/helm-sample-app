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
        stage('Helm Deploy') {
            steps {
                echo 'Deploying to Kubernetes...'
                sh """
                    helm upgrade --install helm-example charts/helm-example \
                    --namespace jenkins \
                    --wait
                """
            }
        }
    }
}
