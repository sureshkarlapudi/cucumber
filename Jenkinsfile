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
     userRemoteConfigs: [[credentialsId: 'dc3086ac-7c03-4ba1-971c-67f6de73edf9',
     url: 'https://github.com/sureshkarlapudi/cucumber.git']]])
 }
def stages = "${env.WORKSPACE}/pipeline_stages"
echo "${env.WORKSPACE}/pipeline_stages"
switch ("${BRANCH_NAME}".toUpperCase()) {
 
    case "MASTER": 
      load "${stages}/build"
      break;
    case "suresh":   
      load "${stages}/build"
      break; 
}

}

} 
