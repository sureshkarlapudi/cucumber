#!groovy
import static java.util.UUID.randomUUID
def generateGUID() {
	uuid = randomUUID() as String
	uuid.toUpperCase()
}
node ("master") 
{
env.UUID = generateGUID()
ws("/work/jenkins/workspace/${JOB_NAME}"){
 stage ("checkout") {
     echo "${env.UUID}"
     checkout([$class: 'GitSCM',  
     branches: [[name:"*/${BRANCH_NAME}"]],
     userRemoteConfigs: [[credentialsId: '2c41666e-f3bf-4e4b-a77c-80e7805de1d4',
     url: 'https://github.com/Hariprasadnaidu/cucumberbasic.git']]])
 }
def stages = "${env.WORKSPACE}/pipeline_stages"
echo "${env.WORKSPACE}/pipeline_stages"
switch ("${BRANCH_NAME}".toUpperCase()) {
 
    case "MASTER": 
      load "${stages}/build"
      break;
    case "DEVELOP":   
      load "${stages}/build"
      break; 
}

}

} 
