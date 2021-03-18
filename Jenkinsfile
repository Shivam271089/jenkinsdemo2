pipeline {
  agent any
  parameters {
  	string(name:'MAVEN_SETTINGS_XML')
  	string(name:'username')
  	string(name:'password')
  	string(name:'appname')
  	string(name:'env')
  	string(name:'workerType')
  	string(name:'workers')
  	string(name:'workerType')
  	string(name:'businessGroup')
  	
  }
  stages {
    stage('Project Build') {
      steps {
        bat "mvn -s ${params.MAVEN_SETTINGS_XML} clean install"
      }
    }
    

    
    stage('Deploy CloudHub') {
     
      steps {
 
      echo "*************CloudHub Deployment start**************"
        bat "mvn clean package deploy -Dmule.version=4.3.0 -Dusername=${params.username} -Dpassword=${params.password} -Denvironment=${params.environment} -Dappname=${params.appName} -Dworkers=${params.workers} -Dworker.type=${params.workerType} -DmuleDeploy -DskipTests"
      }
      
    }
    
  }
}