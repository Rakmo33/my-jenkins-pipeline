pipeline {
  agent any
  stages{
    stage("Initialize"){
      steps{
        dir("./scripts"){
            sh "npm i"
            sh "ls"
            sh "node -v"
            sh "node ./ExcelComparator.js '../results/pv05.xls' '../results/pv07.xls'"
        }
      }
    }
  }
  post {
        always {
            archiveArtifacts 'results/*.xls'
        }
    }
}
