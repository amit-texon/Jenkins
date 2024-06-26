pipeline {
  agent any stages {
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

    stage('Parallel Stages') {
      steps {
        parallel("first"
                 : {echo "first ..."}, "second"
                 : {echo "second ..."}, "third"
                 : {echo "third ..."})
      }
    }
    if (env.BRANCH_NAME == 'dfasdfasdf') {
      stage('staging') {
        steps {
          echo "stagging stage ...."
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
    always{echo "always ..."} success{echo "success ..."} failure {
      echo "failure ..."
    }
  }
}
