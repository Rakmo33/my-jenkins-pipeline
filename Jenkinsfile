pipeline {
  agent any
  stages{
    stage("Initialize"){
      steps{
        sh "pwd && rm -rf my-folder"
        sh "mkdir my-folder"
        sh "cd ./my-folder && pwd"
        sh "pwd"
        dir("./my-folder"){
          sh "pwd"
        }
        sh "pwd"
      }
    }
  }
}
