#!groovy
import static java.util.UUID.randomUUID
def generateGUID() {
	uuid = randomUUID() as String
	uuid.toUpperCase()
}
node ("master") 
{
env.UUID = generateGUID()
ws("C:/Users/HARI/.jenkins/workspace/${JOB_NAME}"){
 stage ("checkout") {
     echo "${env.UUID}"
     checkout([$class: 'GitSCM',  
     branches: [[name:"*/${BRANCH_NAME}"]],
    // userRemoteConfigs: [[credentialsId: '3981e21b-4a8c-498c-9506-d99d775df168',
     url: '<path of git repo>.git'])
 }
def stages = "${env.WORKSPACE}/pipeline_stages"
echo "${env.WORKSPACE}/pipeline_stages"
switch ("${BRANCH_NAME}".toUpperCase()) {
 
    case ~/^master\/.*$/: 
      load "${stages}/build"
    // load "${stages}/test"
      break;
    case "DEVELOP":   
      load "${stages}/build"
      break; 
      /*load "${stages}/test"
      load "${stages}/artifact_upload"
      load "${stages}/deploy_dev"
           
    case ~/^BUGFIX\/.*$/:    
      load "${stages}/build"
      load "${stages}/artifact_upload"
      load "${stages}/deploy_dev"
      break;  
    case ~/^RELEASE\/.*$/:    
      load "${stages}/build"
      load "${stages}/test"
      load "${stages}/artifact_upload"
      load "${stages}/securityscan"
      load "${stages}/deploy_test"
      break;   
    
    case ~/^HOTFIX\/.*$/:   
      load "${stages}/build"
      load "${stages}/artifact_upload"
      load "${stages}/deploy_test"
      break;*/

      
  }
load "${stages}/workspace_cleanup"
}

} 
