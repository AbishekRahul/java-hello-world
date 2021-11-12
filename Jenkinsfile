node {
  stage('SCM Checkout'){
    git 'https://github.com/AbishekRahul/java-hello-world'
  }
  stage('Compile Package'){
    echo 'Compiling the code'
    sh 'mvn package'
  }
}
