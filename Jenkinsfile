node
{
	
		
	stage('Checkout')
	{   

        checkout([$class: 'GitSCM', 
        branches: [[name: '*/master']],
        extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/ramisetty1/k8s-code.git']]])
		
	}
	
	stage('dockerimage')
    {
        app = docker.build("ramisetty32/flask")
    }
	
	stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
        }
    }
    
    stage('Trigger ManifestUpdate') {
                echo "triggering updatemanifestjob"
                build job: 'updatemanifest', parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
        }
    
}
