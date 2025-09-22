pipeline {
agent any
  stages {
     stage('Build')
          {
            steps{
                  sh 'docker build -t varalakshmi5701/repo:bank .'
                 }
           }
     stage('Registry') {
            steps {
               withDockerRegistry(credentialsId: 'docker-registry', url: 'https://hub.docker.com/repositories/varalakshmi5701') {
                       sh 'docker push varalakshmi5701/repo:bank'
                 }
            }
        }
    stage('Deploy')
       {
          steps {
                  sh 'docker run -itd --name cont1 -p 1111:80 varalakshmi5701/repo:bank'
               }
        }
  }
}
