pipeline{
  agent any 
      environment {
        registry = "mhodali/task-3"
        dockerImage = ''
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


      
    }
  }
