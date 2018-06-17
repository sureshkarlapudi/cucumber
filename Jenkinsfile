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
     userRemoteConfigs: [[credentialsId: '9f892948-b36e-46c7-bebb-795c73e8e20c',
     url: 'https://github.com/Hariprasadnaidu/cucumberbasic.git']]])
 }
def stages = "${env.WORKSPACE}/pipeline_stages"
echo "${env.WORKSPACE}/pipeline_stages"
switch ("${BRANCH_NAME}".toUpperCase()) {
 
    case ~/^master\/.*$/: 
      load "${stages}/build"
      break;
    case "DEVELOP":   
      load "${stages}/build"
      break; 
}

}

} 
