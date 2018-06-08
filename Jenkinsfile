pipeline {
  agent any
  tools {
    maven 'm3'
    jdk 'jdk10'
    fossa 'fossa'
  }
  stage('Build') {
    git 'https://github.com/casciom-work/webhook-test.git'
    sh "mvn install -DskipTests"
  }
}