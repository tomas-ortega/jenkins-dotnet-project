pipeline {  
    agent { 
        node { 
                label 'master' 
             } 
    }

    options {
        timestamps()
    }

    stages {
        stage('Clean WorkSpace') {
            steps {
                cleanWs()
            }
        }
        
        stage('Prepare Environment') {
            steps {
                git branch: '$BRANCH_NAME', url: 'https://github.com/tomas-ortega/jenkins-dotnet-project.git'
            }
        }

        stage('Compile Project') {
            steps {
                sh 'dotnet build jenkins-dotnet-project'
            }
        }

        stage('Unit Testing') {
            steps {
                sh 'dotnet test jenkins-dotnet-project'
            }
        }

        stage('Build as a Nugget Package') {
            steps {
                sh 'dotnet pack jenkins-dotnet-project'
            }
        }
    }
}
