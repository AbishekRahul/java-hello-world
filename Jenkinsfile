pipeline {
 agent any
 stages {
     stage('SCM Checkout') {
       steps {
         cleanWs()
         git url: 'https://github.com/AbishekRahul/java-hello-world.git',
         credentialsId: 'a4f2f90b-7f5d-4440-a37d-3c73d30aa3bb'
         sh  "echo pwd"
    }
    }
     stage('MVN Build') {
         steps {
             sh "mvn clean install"
         }
     }
     stage('MVN Test') {
         steps {
             sh "mvn test"
         }
     }
     stage('Sonar Analysis') {
     withSonarQubeEnv('sonar', envOnly: true) {
  // This expands the evironment variables SONAR_CONFIG_NAME, SONAR_HOST_URL, SONAR_AUTH_TOKEN that can be used by any script.
  println ${env.SONAR_HOST_URL} 
  }
     }
 }
}
