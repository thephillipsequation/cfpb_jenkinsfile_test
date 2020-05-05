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
                script {
                    PR = sh(
                            script: "curl https://api.github.com/repos/muchniki/cfpb_jenkinsfile_test/pulls/${env.CHANGE_ID}",
                            returnStdout: true
                    )
                }
              echo "Expect ORIGINAL: ${env.TEST_VAR}"
              sh "echo the PR is ${PR}"
                }
        }
        stage('Env modification') {
            steps {
                withEnv(["TEST_VAR=${TEST_VAR}"]) {
                    sh 'echo PR'
                    sh 'env|sort'
                }
            }
        }
    }
}
