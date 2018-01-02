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
              echo "${env.TEST_VAR}"
                }
        }
        stage('Modified') {
            steps {
                withEnv(['TEST_VAR=urmom']) {
                    sh 'echo $TEST_VAR'
                }
            }
        }
        stage('Shell Modification') {
            steps {
                script {
                    TEST_VAR = sh(
                      script: 'date -u +%s',
                      returnStdout: true
                    )
                }
                echo "${TEST_VAR}"
                echo "${env.TEST_VAR}"
                sh 'echo $TEST_VAR'
            }
        }
        stage('Env modification') {
            steps {
                withEnv(["TEST_VAR=${TEST_VAR}"]) {
                    echo "${env.TEST_VAR}"
                    sh 'echo $TEST_VAR'
                }
            }
        }
    }
}
