
pipeline {
agent any

     
     
    
    stages {  

        stage ("Clone Repository") {
                steps {
                   git branch: 'master', url: 'https://github.com/Swadhin1997/testrepo2.git'
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
               sh "dotnet build testwebapp.sln"
            }           
        } 
    }
} 
