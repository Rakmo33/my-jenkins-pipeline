pipeline {
  agent any
  stages{
    stage("Initialize"){
      steps{
        dir("./scripts"){
            sh "npm i"
            sh "node -v"
        }
        sh "pwd"
      }
    }
  }
}
