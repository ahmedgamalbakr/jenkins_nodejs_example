pipeline {
    agent {
        label 'aws'
    }
    
    stages {
   
        stage('Build') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'DOCKER_HUB_USERNAME', passwordVariable: 'DOCKER_HUB_PASSWORD')]) {
                    sh 'docker build . -f dockerfile -t ahmedhgamal22/myapp'
                    sh 'docker login -u $DOCKER_HUB_USERNAME -p $DOCKER_HUB_PASSWORD'
                    sh 'docker push ahmedgamal22/myapp:latest'
                }
            }
        }
    }
}

