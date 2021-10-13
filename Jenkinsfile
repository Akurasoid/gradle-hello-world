node (‘slave1’) {
  stage ('Checkout'){
      checkout scm
   }
  stage ('Build'){
  def gradleHome = tool 'gradle4'
    sh "${gradleHome}/bin/gradle clean install"
  }
}
