pipeline {
    agent any
    environment {
      TEST_VAR = sh(
          returnStdout: true,
          script: "echo 'ORIGINAL'"
          )
    }
    stages {
        stage('Original') {
            steps {
              echo $TEST_VAR
                }
            }
        stage('modified') {
            steps {
                withEnv([TEST_VAR='modified']) {
                  sh 'echo $TEST_VAR'
                }
            }
        }
    }
}
