
@Library('piper-library-os') _


node()
{
stage('Prepare')	
	checkout scm
	
  stage('DeployCommit') 
    gctsDeploy(
  script: this,
  host: 'https://hclutl1909.hcldigilabs.com:8001',
  abapCredentialsId: 'ABAPUserPasswordCredentialsId',
  repository: 'hcl-devops-v2',
  remoteRepositoryURL: "https://github.com/abhilashhaa/HCL-DevOPs-V2.git",
  role: 'TARGET',
  vSID: 'FEF',
  rollback: 'false'
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
