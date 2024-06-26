pipeline {
  agent any 
  try {
    stages {
      stage('test'){
          echo "test stage .... from SCM ..."
          
      }

      stage('build') {
        echo "build stage" 
        try { 
            echo "try block changes...." 
            
        } catch (e) {
          echo "Error: ${e.message}"
        }
      }

      stage('Parallel Stages') {
        parallel(
            "first": {echo "first ..."}, 
            "second": {echo "second ..."}, 
            "third": {echo "third ..."})
      }
      if (env.BRANCH_NAME == 'dfasdfasdf') {
        stage('staging') {
          echo "stagging stage ...."
        }
      }

      stage('test-deploy') {
          echo "test-deploy stage ..."
          
      }

      stage('prod-deploy') {
        echo "prod-deploy stage ...."
      }

    
    }
  } catch (Exception e) {
    echo "Error: ${e.message}"
  }

  post {
    always {
        echo "always ..."
    }
    success {
        echo "success ..."
    }
    failure {
        echo "failure ..."
    }
  }
}
