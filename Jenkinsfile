@Library("CitrixSharedLibrary") _
import java.text.SimpleDateFormat
import java.util.Date
import groovy.json.JsonOutput
import groovy.json.JsonSlurperClassic
node("docker && linux") {
  deleteDir()
  
  pacmanWithGitCredentials.httpGitCredentials("github-app-boz") {
        checkout([$class: 'GitSCM', branches: [[name: 'master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-app-boz11', url: 'https://github.com/bozangnj/test-action.git']]])
        sh "ls"
        sh "git status" 
        sh "git checkout master"
        sh "git branch"
        sh "git pull origin master"
        writeFile file: "lastDeployDateOfPacmanEa", text: "hello"
        sh "git add lastDeployDateOfPacmanEa; git commit -m 'update the ea deploy time' --allow-empty; git push -u origin master"
      }
  
}
