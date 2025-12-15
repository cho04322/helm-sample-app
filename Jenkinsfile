pipeline {
    agent {
        kubernetes {
            yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    role: builder
spec:
  serviceAccountName: default  # [중요] 아까 권한을 준 SA 이름 (기본은 default)
  containers:
  - name: helm
    image: alpine/helm:3.11.1  # [정석] Helm이 포함된 공식 이미지 사용
    command:
    - cat
    tty: true
"""
        }
    }    
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
                container('helm') {
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
}
