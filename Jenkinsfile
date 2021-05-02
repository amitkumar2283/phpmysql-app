node{
    stage('SCM Checkout')
    {
        git url: 'https://github.com/amitkumar2283/phpmysql-app'
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
            sh "sudo docker login -u devopsxprts -p ${DHPWD}"
        }
        sh 'sudo docker tag phpwebapp_web devopsxprts/phpmysql_app'
        sh 'sudo docker push devopsxprts/phpmysql_app'
    }
}
