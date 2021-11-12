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
     stage('SonarQube Analysis') {
      steps{
      withSonarQubeEnv() {
      sh "mvn clean verify sonar:sonar"
    }
  }
     }
}
}
