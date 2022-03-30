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
            emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
                subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
        }
 }
}
