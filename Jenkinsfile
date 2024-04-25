import jenkins.model.Jenkins

pipeline {
  agent any
  stages{
    stage("Initialize"){
      steps{
        dir("./scripts"){
            sh "npm i"
            sh "ls"
            sh "node -v"
          
            def artifacts = getArtifactsWithPrefixAndSuffix('my-jenkins-pipeline', 'pv', '.xls') 
            sh "echo artifacts"
            sh "node ./ExcelComparator.js artifacts[0] artifacts[1]"
          
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


def getArtifactsWithPrefixAndSuffix(String jobName, String prefix, String suffix) {
    def buildInfo = Jenkins.instance.getItemByFullName(jobName).getLastSuccessfulBuild()
    if (buildInfo != null) {
        def artifacts = buildInfo.getArtifacts()
        def filteredArtifacts = artifacts.findAll { artifact ->
            artifact.relativePath.startsWith(prefix) && artifact.relativePath.endsWith(suffix)
        }
        return filteredArtifacts.collect { "${SERVER_URL}/job/${jobName}/${buildInfo.getNumber()}/artifact/${it.relativePath}" }
    }
    return []
}
