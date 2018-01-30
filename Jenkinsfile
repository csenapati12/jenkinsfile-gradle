node()
{
	
	parameters {
        booleanParam(defaultValue: false, description: '', name: 'userFlag')
	string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    }
    try	{
	   // echo  "Branch Name is ${BRANCH_NAME}" 
	        if (env.BRANCH_NAME == 'develop') 
			{
			 print "Building the develop branch "
			 developBranch()
			}
		
	           else if (env.BRANCH_NAME == 'master') 
			{
			 print "Building the master branch "
			//calling the function masterBranch if master branch is getting built
			 masterBranch()
			}
	           else  
			{
			 print "Building the feature branch"
			//calling the function featureBranch if feature branch is getting built
			 featureBranch()
			}
		
		} 
	catch(e) 
		{
		currentBuild.result = "FAILED"	
		//notifyBuild(currentBuild.result)
		throw(e)
		} 
    finally 
		{
		sh "echo final block"
		}	
 }

def developBranch() 
{
 echo "inside DEVELOP"
}

def masterBranch() 
{
 echo "inside MASTER"
}

def featureBranch() 
{
 echo "inside FEATURE"
	stage 'Prepare'
	//loadProperties()
	loadProperties1()
	stage 'Checkout'
	checkout_code()
	stage 'Build'
	//withMaven(maven: 'apache Maven 3.3.9'){
	//sh 'mvn clean compile'
	//}
	sh 'gradle hello1'
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
		echo "***********Building Code************Java version ${Var1}" 
		//checkout scm
	}
def build_code()
	{
	echo "***********Building Code************Maven version ${Var2}"  
          //echo "*******getting value ${maven}*********"
         // sh 'cd C:/learning/software-dump/gradle-4.1-bin/practice'
          //sh 'gradle hello1'   
}


	 
