pipeline{
  agent any 
      environment {
        registry = 'mhodali/server'
        dockerImage = ''
        registryCredential='server'
    }
    
    stages{
 stage("clone"){
        steps{
checkout([$class: 'GitSCM', extensions: [], userRemoteConfigs: [[ url: 'https://github.com/mhodali/server.git']]])
        }}
      
      stage("build"){
        steps{
        script {
          dockerImage = docker.build registry
        }}}
stage('Push image') {
           steps{
        script {
  docker.withRegistry( '', registryCredential ) {
        dockerImage.push() 
           }}}}
      stage("run"){
        steps{
 
         sh './create-server.sh'
        }}
      
    }
  }
