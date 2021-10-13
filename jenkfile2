pipeline {
    agent any
    tools { 
        gradle 'gradle4'
    }
    stages {
      stage('checkout') {
        steps {
          checkout scm
        }
      }
      stage('build') {
        steps {
          echo "Path is" + env.PATH
          sh "gradle build"
        }
      }
    }
}
