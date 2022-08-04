pipeline 
{
    agent any

    environment{
        imageName = "pankajpatre11/myapp"
        registryCredentials = "nexusid"
        registry = "54.226.252.254:8083"
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
                       docker.withRegistry('http://'+registry, registryCredentials)
                           {
                           dockerImage.push("latest")
                            }
	                }   
             }
            
         }	    
	    
    }
}



