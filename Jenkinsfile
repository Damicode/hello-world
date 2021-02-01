pipeline {
  agent any
  tools {
  
  maven 'maven'
   
  }
    stages {

      stage ('Checkout SCM'){
        steps {
          checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: []])
        }
      }
	  
	  stage ('Build')  {
	      steps {
          
           
 
            sh "mvn package"
 
          
        }
         
      }
   
      stage ('SonarQube Analysis') {
        steps {
              withSonarQubeEnv('sonar') {
                
				
 
                 sh 'mvn -U clean install sonar:sonar'
                
 
                
				
              }
            }
      }
      
      
      
   

 

 
    }

 

    stage('Waiting for Approvals') {
            
        steps{

				input('Test Completed ? Please provide  Approvals for Prod Release ?')
			  }
            
    }     


 
         
   } 
}

