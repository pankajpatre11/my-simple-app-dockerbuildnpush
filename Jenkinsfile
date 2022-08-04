pipeline 
{
    agent any

    environment{
	SONAR_TOKEN = "ebe715a7d0fdd4ffb924ae703699a6131009211a"
	GIT_COMMIT_SHORT = sh(
     script: "printf \$(git rev-parse --short ${GIT_COMMIT})",
     returnStdout: true)
        imageName = "pankajpatre11/myapp"
        registryCredentials = "dockerhub"
        registry = "18.208.249.204:8083"
        dockerImage = ''
    }
    options {
       buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '7')
       }
    stages
    {
  
        stage('Build Docker image')
        {
            steps
            {
                script{
                    dockerImage = docker.build(imageName)
                }
            }
         }
      stage('Upload Docker image into Repo')
        {
            steps
            {
                script{ 
			sh 'docker tag myapp pankajpatre11/myapp'			
			sh 'docker login -u pankajpatre11 -p Pankaj@2211' 
		        sh 'docker push pankajpatre11/myapp' 
			sh 'pwd'
                 // docker.withRegistry("https://docker.io/pankajpatre11", "dockerhub")
                  // {
	           // sh 'docker tag myapp docker.io/myapp'
                    //sh 'docker images'
                   // dockerImage.push("latest")
                  // }
                }
            }
         }	    
	    
    
	    
    }
}



