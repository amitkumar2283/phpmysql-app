node{

    stage('SCM Checkout')
    {
        git credentialsId: '4cc785e9-441d-4818-a248-2bfb2148004d', url: 'https://github.com/VardhanNS/phpmysql-app.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'sudo docker-compose build'
        sh 'sudo docker-compose down'
        sh 'sudo docker-compose up -d'
    }
    stage('PUSH image to Docker Hub')
    {
        withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) 
        {
            sh "docker login -u vardhanns -p ${DHPWD}"
        }
        sh 'docker push vardhanns/phpmysql_app'
    }
}
