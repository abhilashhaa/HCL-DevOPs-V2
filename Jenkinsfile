
@Library('piper-library-os') _


node()
{
stage('Prepare')	
	checkout scm
	
  gctsDeploy(
  script: this,
  host: 'https://hclutl1909.hcldigilabs.com:8001',
  client: '200',
  abapCredentialsId: 'ABAPUserPasswordCredentialsId',
  repository: 'hcl-devops-v',
  remoteRepositoryURL: "https://github.com/abhilashhaa/HCL-DevOps-V1.git",
  role: 'TARGET',
  vSID: 'FEF',
  rollback: true,
  configuration: [VCS_AUTOMATIC_PULL: 'FALSE',VCS_AUTOMATIC_PUSH: 'FALSE',CLIENT_VCS_LOGLVL: 'debug']
)

	      
	
stage('RunUnitTest')
	 { 
  try { 
	  gctsExecuteABAPUnitTests(
      script: this,
      host: 'https://hclutl1909.hcldigilabs.com:8001',
      client: '200',
      abapCredentialsId: 'ABAPUserPasswordCredentialsId',
      repository: 'hcl-devops-v2'
	  )
	 currentBuild.result = 'SUCCESS'
 	  } 
	catch (Exception err) { currentBuild.result = 'FAILURE'
	     } 
echo "RESULT: ${currentBuild.result}"
		 
		 }
	
   stage("Rollback")
	{
	if (currentBuild.result == 'FAILURE')
		{
	steps:
	    script {
	       gctsRollback(
        script: this,
        host: "https://hclutl1909.hcldigilabs.com:8001",
        client: "200",
        abapCredentialsId: 'ABAPUserPasswordCredentialsId',
        repository: "hcl-devops-v2"
   )
		    
		    
	    }
		}
	       
	}
	

	
                     
        
  
	

}
