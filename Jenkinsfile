pipeline {
agent any
     options {
        
    stages {  

        stage ("Clone Repository") {
                steps {
                   git branch: 'main', url: 'https://github.com/Swadhin1997/demodotnet.git'
                }
            }  
        stage('Prep') {
            steps {
                script {
                    GIT_BRANCH=sh(returnStdout: true, script: 'git symbolic-ref --short HEAD').trim()
                    currentBuild.setDisplayName("#${currentBuild.number} [" + GIT_BRANCH + "]")
                    sh "export GIT_BRANCH=$GIT_BRANCH"
                }
            }
        }  
        stage ('Building dll') {
            steps {
               sh "dotnet build Demo.sln"
            }           
        }
    }
    
