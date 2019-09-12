

node {

  try {
  
  stage('Code Checkout') { 
      // Get some code from a GitHub repository
      git 'https://github.com/jitensingh12/calcwebapp.git'

   }
   
   stage('Unit Test') { 
      // Get some code from a GitHub repository
    sh 'mvn test'    
     

   }
   
   stage('Test Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
   
   stage('Package & Deploy') {
   sh 'mvn package'
	 sh '/usr/bin/curl --upload-file target/calcwebapp.war "http://deployer:deployer@6243cfba.ngrok.io/manager/text/deploy?path=/jitendrawebcal&update=true"'
   }
   

} catch(e) {
	echo "Caught some exception"
	
    mail bcc: '', body: '''Jenkins build Failure!!!
	
    Better get it fixed!
    Anand''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'anandr72@gmail.com' 
}  finally {
	echo "Finally Block"
	
	
	
    Build executed!
    

}
    
}
