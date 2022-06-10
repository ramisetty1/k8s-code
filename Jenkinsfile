pipeline {

   agent any
   
   stages {
       stage('checkout') {
            steps {
                echo "this is checkout stage"
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ramisetty1/k8s-code.git']]])
            }
        }
   }
}
    
