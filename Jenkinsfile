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
            emailext subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
                        body: '$DEFAULT_CONTENT',
                        recipientProviders: [
                            [$class: 'CulpritsRecipientProvider'],
                            [$class: 'DevelopersRecipientProvider'],
                            [$class: 'RequesterRecipientProvider']
                        ], 
                        replyTo: '$DEFAULT_REPLYTO',
                        to: '$DEFAULT_RECIPIENTS'
        }
  }
}
