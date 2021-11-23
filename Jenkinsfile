repoUrl = "https://github.com/luishernandez25/easyTest"
branchName = "master"

pipeline {
    agent {
        node("builder")
    }

    stages {
        stage('Clone') {
            steps {
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

        stage('Build'){
            steps{
                //update resources
                dir('build') {
		            sh 'mvn build'
                }
		        //run test    
                //sh 'mvn test -Dtest='+ testSuite 
            }
        }
    }
}
