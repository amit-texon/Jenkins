pipeline {
  agent any 

  parameters {
        string(name: 'NAME', description: 'Please tell me your name')
        choice(name: 'GENDER', choices: ['Male', 'Female'], description: 'Choose Gender')
    }
  
  stages {
    stage('test') {
      steps {
        echo "test stage .... from SCM ..."

        script {
                    def name = "${params.NAME}"
                    def gender = "${params.GENDER}"
                    if(gender == "Male") {
                        echo "Mr. $name"    
                    } else {
                        echo "Mrs. $name"
                    }
                }
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
