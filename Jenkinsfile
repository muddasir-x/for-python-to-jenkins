pipeline {
    agent any 
    
    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/muddasir-x/for-python-to-jenkins.git'
            }
        }
        
        stage('build docker') {
            steps {
                sh 'docker build -t auto-deploy-web .'
            }
        }
        
        stage('depoly container') {
            steps {
                sh '''
                docker rm -f  auto-deploy-web || true
                docker run -d -p 5000:5000 --name auto-deploy-web auto-deploy-web
            }
        }
    }
    post {
        always {
            echo "pipelines build it"
        }
        success {
            echo "pipeline successfully hogayi hai"
        }
        failure {
            echo "pipelines failed hogayi hai do it again boy "
        }
    }
}
