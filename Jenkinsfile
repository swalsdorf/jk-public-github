pipeline {
    agent any

    stages {
        stage('cloning git repository') {
            steps {
                git branch: 'main', url: 'https://github.com/swalsdorf/jk-public-github.git'
            }
        } 
        
        stage('building image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        
        
        stage('Deploying Application') {
            steps {
                sh '''
                # docker stop webapp_ctr
                docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}
            '''
            }
        }
    }
}
