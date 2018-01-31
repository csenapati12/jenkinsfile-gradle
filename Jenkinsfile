node()
{
	
	//parameters {
        //booleanParam(defaultValue: false, description: '', name: 'userFlag')
	//string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
   // }
   
 

	stage 'Prepare'
	//loadProperties()
	loadProperties1()
	stage 'Checkout'
	checkout_code()
	stage 'Build'
	build_code()
	stage 'Uploading Artifacts'
	archiveArtifacts()
	stage 'Email Notification'
	notifyBuild()
	

	//withMaven(maven: 'apache Maven 3.3.9'){
	//sh 'mvn clean compile'
	//}
	//sh 'gradle hello1'
}
def loadProperties() {
	echo "Inside Prepare"

        properties = null
        checkout scm
	echo "Immediate one ${userFlag}"
	echo "${params.Greeting} World!"
	echo  "WORKSPACE NAME Name is ${workspace}"
        properties = new Properties()
	echo "1-------------"
        File propertiesFile = new File("${workspace}/gradle.properties")
	echo "2-------------"
        properties.load(propertiesFile.newDataInputStream())
	echo "3-------------${java}"
	
       
  
}


def loadProperties1(){
	checkout scm
def props = readProperties  file:"${workspace}/gradle.properties"
def Var1= props['java']
def Var2= props['maven']
//echo "Var1=${Var1}"
//echo "Var2=${Var2}"
echo  "WORKSPACE NAME Name is ${workspace}"
	echo  "First property is ${Var1} and second property is =${Var2}"

}
def checkout_code()
	{
		echo "checkout_code"
		echo "***********Building Code************" 
		//checkout scm
	}
def build_code()
	{
	echo "***********Building Code************"  
          //echo "*******getting value ${maven}*********"
         // sh 'cd C:/learning/software-dump/gradle-4.1-bin/practice'
          //sh 'gradle hello1'   
}

def archiveArtifacts()
	{
	echo "**********Archiving the artifacts *********"
        //sh 'make' 
         //archiveArtifacts artifacts: '**//*.zip', fingerprint: true 
}
 
/*** Sending the Email Notification ***/
	
	def notifyBuild()
	{
		
        buildStatus =  buildStatus ?: 'SUCCESSFUL'

        def subject = "${buildStatus}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'"
        def emailBody = '${JELLY_SCRIPT, template="jenkins-email"}'
		
		/*** Add the set of email address for the Notification ***/
        def recipientList = "id to be added"  
    
        emailext (subject: subject,body: emailBody,to: recipientList,mimeType: 'text/html')
 }

	 
