import groovy.xml.*;
import groovy.util.*;
node('master'){
checkout scm
	echo "Before build"
props = readYaml file: 'Jenkinsfile.yaml'
library 'pipeline-build' //REQUIRED TO MAKE mavenBuild GLOBAL FUNCTION AVAILABLE
	BUILD_NUMBER = env.BUILD_NUMBER
		buildNum = BUILD_NUMBER
		version = "${props.appVersion}.${buildNum}"
        echo "${version}"
		//Build
	    stage('build'){
				runBuild(props,buildNum)
	    }
}//end node	

def runBuild(props,buildNum){
	mavenBuild{
		pomFileLocation = props.pomFileLocation
		appVersion = props.appVersion
		artifactBuildNumber = buildNum
	}
}	
