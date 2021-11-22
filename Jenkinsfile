// String branchName = env.BRANCH_NAME
String branchName = "master"
// String gitCredentials = "CREDENTIAL_ID"
String repoUrl = "https://github.com/luishernandez25/easyTest"

node {
  // Start Stages   
  stage('Clone') {
      // Clones the repository from the current branch name
      echo 'Make the output directory'
      sh 'mkdir -p build'

      echo 'Cloning files from (branch: "' + branchName + '" )'
      dir('build') {
          // git branch: branchName, credentialsId: 	gitCredentials, url: repoUrl
          git branch: branchName, url: repoUrl
      }     
  }       
}