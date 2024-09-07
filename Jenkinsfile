def dockerImageTag = "peketi/jenkins:v2-${BUILD_NUMBER}"

node {
   
    stage('Checkout') {
        
        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/PeketiBrahamaReddy/docker-1.git']])
       
    }
    stage('DockerImageBuild') {
        def dockerImage = docker.build(dockerImageTag)
      
    }
    stage('Push to DockerHUB') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerHUB') {
        def dockerImage = docker.image(dockerImageTag)
        dockerImage.push()
     }
    }
}
