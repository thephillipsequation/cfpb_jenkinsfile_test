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
                          script: "curl https://api.github.com/repos/imuchnik/cfpb_jenkinsfile_test/pulls/${env.CHANGE_ID} | jq .state",
                            returnStdout: true
                    )
                }
              sh "echo the PR is ${PR}"
                }
        }
        stage('Env modification') {
            steps {
                withEnv(["TEST_VAR=${TEST_VAR}"]) {
                    sh 'echo PR status is $PR'
                    sh 'env|sort'
                }
            }
        }
    }
}
