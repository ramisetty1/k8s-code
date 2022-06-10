pipeline {
    environment {
    imagename = "ramisetty32/flask"
    DOCKERHUB_CREDENTIALS=credentials('dockerhub')
   
  }

   agent any
   
   stages {
       stage('checkout') {
            steps {
                echo "this is checkout stage"
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ramisetty1/k8s-code.git']]])
            }
        }
      
        stage('Docker Image Build'){
                steps{
                    script{
                        docker.build imagename + ":$BUILD_NUMBER"
                    }
                }
  
}
}
    
