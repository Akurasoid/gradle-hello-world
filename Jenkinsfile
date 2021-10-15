node('slave1') { 
 gradle4 = tool 'gradle4'
 currentBuild.result = "SUCCESS"
 try {
  stage ('checkout'){
     checkout scm
  }
  stage ('build')
  {
      sh "${gradle4}/bin/gradle build"
  }
 } catch (ex) {
  currentBuild.result = "FAILURE"
  echo 'Error occured'
 }
 stage('post') {
  echo "Build result is " + currentBuild.result
  if ( currentBuild.result == 'SUCCESS') {
   addBadge(icon: 'green.gif', text: 'Build Succeeded')
  }
  if (currentBuild.result == 'FAILURE') {
   addBadge(icon: 'red.gif', text: 'Build Failed')
  } 
  stage('unit-test') {
     sh "gradle clean test"
     junit 'build/test-results/junit-platform/*.xml'
     archiveArtifacts artifacts: 'build/libs/**/*.jar'
  }
  stage('func-test') {
     
 }
 }
}
