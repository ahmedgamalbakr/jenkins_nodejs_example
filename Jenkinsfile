pipeline {
    agent {
        label 'aws'
    }
    
    stages {
   
        stage('Build') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'username', passwordVariable: 'password')]) {
                    sh 'docker build . -f dockerfile -t ahmedgamal22/myapp'
                    sh 'docker login -u ${username} -p ${password}'
                    sh 'docker push ahmedgamal22/myapp'
                }
            }
        }
    }
}


