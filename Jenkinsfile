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

        stage('Deploy to Kubernetes') {
             steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    sh "kubectl apply -f appDeploy.yaml"
                }
        }
    }
  }
}

