@Library("CitrixSharedLibrary") _
import java.text.SimpleDateFormat
import java.util.Date
import groovy.json.JsonOutput
import groovy.json.JsonSlurperClassic


node("docker && linux") {
  deleteDir()
  dir("${env.WORKSPACE}/pacman_config") {
   withCredentials([usernamePassword(credentialsId: "github-app-boz")]) {
          checkout([$class: 'GitSCM', branches: [[name: 'master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-app-boz', url: 'https://github.com/bozangnj/test-action.git']]])
          sh "ls"
          sh "git status" 
          sh "git config --global user.email 'boz@citrix.com'"
          sh "git config --global user.name 'boz'"
          sh "git checkout master"
          sh "git branch"
          writeFile file: "lastDeployDateOfPacmanEa", text: "hello"
          sh "ls"
          sh "git add lastDeployDateOfPacmanEa; git commit -m 'update the ea deploy time' --allow-empty; git push -u origin master"
        }
  }
}
