pipeline 
{
    agent any

    environment{
        imageName = "pankajpatre11/myapp"
        registryCredentials = "nexusid1"
        registry = "35.172.201.214:8083"
        dockerImage = ''
    }
    options {
       buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '7')
       }
    stages
    {
  
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



