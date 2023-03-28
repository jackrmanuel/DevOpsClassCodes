pipeline{
	agent any
	tools{
	    maven 'maven'
	}
      stages{
           stage('Checkout'){
	    
               steps{
		         echo 'cloning..'
                 git 'https://github.com/jackrmanuel/DevOpsClassCodes'
              }
          }
          stage('Compile'){
             
              steps{
                  echo 'compiling..'
                  sh 'mvn compile'
	      }
          }
          stage('CodeReview'){
		  
              steps{
		          echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('UnitTest'){
		  
              steps{
	              echo 'UnitTest'
                  sh 'mvn test'
              }
               post {
               success {
                   junit 'target/surefire-reports/*.xml'
               }
           }	
          }
          
          stage('Package'){
		  
              steps{
                  sh 'mvn package'
              }
          }
      }
}
