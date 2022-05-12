
@Library('piper-library-os') _


node()
{
stage('Prepare')	
	checkout scm
	
  gctsDeploy(
  
)

	      
	
stage('RunUnitTest')
	 { 
  try { 
	  gctsExecuteABAPUnitTests(
 
		 
		 }
	
   stage("Rollback")
	{
	
	steps:
	    script {
	       gctsRollback(
       
   )
		    
		    
	    }
		}
	       
	}
	

	
                     
        
  
	

}
