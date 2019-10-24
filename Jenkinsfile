node('master'){
checkout scm
	echo "Before build"
props = readYaml file: 'Jenkinsfile.yaml'
library 'pipeline-build' //REQUIRED TO MAKE mavenBuild GLOBAL FUNCTION AVAILABLE
		buildNum = common.getGitTimeStampDotGitSha()
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
