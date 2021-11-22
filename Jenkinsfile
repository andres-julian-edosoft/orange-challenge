// String branchName = env.BRANCH_NAME
// String branchName = "master"
// String gitCredentials = "CREDENTIAL_ID"
// String repoUrl = "https://github.com/luishernandez25/easyTest"
pipeline {
  agent {
    kubernetes {
      label 'promo-app'  // all your pods will be named with this prefix, followed by a unique id
      idleMinutes 5  // how long the pod will live after no jobs have run on it
      yamlFile 'build-pod.yaml'  // path to the pod definition relative to the root of our project 
      defaultContainer 'maven'  // define a default container if more than a few stages use it, will default to jnlp container
    }
  }

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

  stage('test') {
      sh "ls -al; pwd"
      sh "ls -la"
  }

  stage('Build') {
      jenkins = fileLoader.load('build/Jenkinsfile')
      jenkins.start()
  }
}
