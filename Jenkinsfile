pipeline {
  agent any 
  stages {
    stage('test') {
      steps {
        echo "test stage .... from SCM ..."
      }
    }

    stage('build') {
      steps {
        echo "build stage" try { echo "try block changes...." } catch (e) {
          echo "Error: ${e.message}"
        }
      }
    }

    

    stage('test-deploy') {
      steps {
        echo "test-deploy stage ..."
      }
    }

    stage('prod-deploy') {
      steps {
        echo "prod-deploy stage ...."
      }
    }
  }

  post {
    always{echo "always ..."} 
    changed {echo "changed "}
    success{echo "success ..."} 
    failure {
      echo "failure ..."
    }
    unstable {echo "unstable"}
  }
}
