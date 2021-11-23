repoUrl = "https://github.com/luishernandez25/easyTest"
branchName = "master"

pipeline {
    agent {
        node("builder")
    }

    // parameters {
    //       choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    //       string(defaultValue: 'master', name: 'BRANCH')
    // }


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
                // Build
                echo "Do something..."

                a = listGitBranches(
                        branchFilter: 'origin.*/(.*)',
                        defaultValue: 'default',
                        name: 'nameOfVariable',
                        type: 'BRANCH',
                        remoteURL: repoUrl)
                echo a

            }
        }
    }
}
