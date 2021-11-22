pipeline {

    agent {
        kubernetes {
        inheritFrom 'mypod'
        yaml '''
      spec:
        containers:
        - name: maven
          image: maven:3.8.1-jdk-11
'''
        }
    }

    stages {
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

        stage('Build'){
            steps{
                //update resources
		        //sh'mvn install'
		        //run test    
                sh 'mvn test -Dtest='+ testSuite 
            }
        }

    }
}
