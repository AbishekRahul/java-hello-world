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
 post {
        always {
            echo 'Sending job status over email!'
            emailext body: '$DEFAULT_CONTENT', recipientProviders: [buildUser(), culprits(), developers(), requestor()], subject: 'Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}', to: 'k.a.rahulabi@gmail.com'
       }
  }
}
