pipeline {

    agent {
        kubernetes {
        yaml '''
            apiVersion: v1
            kind: Pod
            metadata:
            labels:
                some-label: some-label-value
            spec:
            containers:
            - name: maven
                image: maven:alpine
                command:
                - cat
                tty: true
            - name: busybox
                image: busybox
                command:
                - cat
                tty: true
            '''
        }
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
		        //sh'mvn install'
		        //run test    
                sh 'mvn test -Dtest='+ testSuite 
            }
        }

    }
}
