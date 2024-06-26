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
        echo "build stage" 
      }
    }

    

    stage('test-deploy') {
      steps {
        parallel (
            firstTask: {
                echo  "first task ...."
            },
            secondTask: {
                echo "second task ..."
            }
        )

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
