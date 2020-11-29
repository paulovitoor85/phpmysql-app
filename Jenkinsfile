node{

    stage('SCM Checkout')
    {
        git credentialsId: '66759160', url: 'https://github.com/paulovitoor85/phpmysql-app.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'docker-compose build'
        sh 'docker-compose up -d'
    }
    stage('PUSH image to Docker Hub')
    {
        withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) 
        {
            sh "docker login -u paulovitoor85 -p ${DHPWD}"
        }
        sh 'docker push paulovitoor85/phpmysql_app'
    }
}
