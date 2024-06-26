@Library('shared-library') _

pipeline {
  agent any 

/*  triggers {
        cron('H 4 * * 1-5')
  } */
  
  parameters {
        string(name: 'NAME', description: 'Please tell me your name')
        string(name: 'WEEKDAY', description: 'Please tell day of week')
        choice(name: 'GENDER', choices: ['Male', 'Female'], description: 'Choose Gender')
  }

  tools {
        maven 'apache-maven-3.0.1' 
  }
  
  stages {
    stage('test') {
      steps {
        echo "test stage ..."
        
        /*sh 'mvn --version'*/
        
        helloWorld(name:"${params.NAME}", dayOfWeek:"${params.WEEKDAY}")
  
        
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
