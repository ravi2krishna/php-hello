pipeline {
    agent any

    environment {
    VERSION ="1.${env.BUILD_NUMBER}"
    }

    stages {
        stage('Build Image') {
            steps {
                script {
                    echo "My Image is ${VERSION}"
                    sh 'docker build -t ravi2krishna/php-hello:${VERSION} .'    
                }
                
            }
        }
        
        stage('Push Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-cred', passwordVariable: 'REGISTRY_PWD', usernameVariable: 'REGISTRY_USER')]) {
                    sh 'docker push ravi2krishna/php-hello:${VERSION}'    
                }
            }
        }
    }
}
