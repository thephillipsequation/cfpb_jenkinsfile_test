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
              echo "Expect ORIGINAL: ${env.TEST_VAR}"
                }
        }
        stage('Modified') {
            steps {
                withEnv(['TEST_VAR=modified']) {
                    echo "Expect modified: ${env.Test_VAR}"
                    sh 'echo expect modified: $TEST_VAR'
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
                echo "Expect epoch: ${TEST_VAR}"
                echo "expect ORIGINAL: ${env.TEST_VAR}"
                sh 'echo expect epoch: $TEST_VAR'
            }
        }
        stage('Env modification') {
            steps {
                withEnv(["TEST_VAR=${TEST_VAR}"]) {
                    echo "expect epoch ${env.TEST_VAR}"
                    sh 'echo expect epoch: $TEST_VAR'
                    sh 'env|sort'
                }
            }
        }
    }
}
