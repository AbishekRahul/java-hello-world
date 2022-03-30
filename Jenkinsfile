pipeline {
 agent any
 tools {
  jdk 'jdk'
  maven 'mvn'
}
 stages {
     stage('MVN Build') {
         steps {
             bat "mvn clean install"
         }
     }
     stage('MVN Test') {
         steps {
             bat "mvn test"
         }
     }
 }
}
