
@Library('piper-library-os') _


node()
{
stage('Prepare')	
	checkout scm
	
Stage('CreatRepo')
	{
		gctsCreateRepository(
  script: this,
  host: 'https://hclutl1909.hcldigilabs.com:8001',
  client: '200',
  abapCredentialsId: 'ABAPUserPasswordCredentialsId',
  repository: 'myrepo',
  remoteRepositoryURL: 'https://github.com/abhilashhaa/HCL-DevOPs-V2.git',
  vSID: 'FEF'
  )
	}
	
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
